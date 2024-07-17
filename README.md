# ansible_cmdb

An Ansible role designed to create a CMDB (Configuration Management Database) table view of all your hosts in the inventory.

## Features

- **Compatibility**: Works seamlessly with any web server.
- **Simple Design**: Utilizes basic JS, HTML, and CSS.
- **Data Storage**: Stores information in JSON and HTML files for easy access and management.

## Overview

![screenshot](docs/assets/overview.png)

- **Sortable List**: Easily sort your data to find what you need quickly.
- **Regex Search**: Powerful search functionality using regular expressions.
- **Customizable**: Fully adaptable to suit your specific requirements.
- **Error Handling**: Displays information about unreachable servers for better troubleshooting.


## Detailed View

![screenshot](docs/assets/detailview.png)

Provides a detailed page for each server with comprehensive information.

## Usage

Include the role in your Ansible playbook:

```yaml
---
- name: CMDB
  hosts: all
  gather_facts: true
  ignore_unreachable: true
  roles:
    - ansible_cmdb
```

Configure settings in your inventory file:

```yaml
ansible_cmdb_webserver_hostname: localhost  # used to delegate the tasks
ansible_cmdb_webserver_path: /var/www/pub/cmdb

ansible_cmdb_webserver_owner: www-data
ansible_cmdb_webserver_group: www-data
ansible_cmdb_webserver_mode_files: '0644'
ansible_cmdb_webserver_mode_folder: '0755'
```

Enable or disable specific reports:

```yaml
# reports
ansible_cmdb_report_hallo_welt: true
ansible_cmdb_report_hostvars: true
ansible_cmdb_report_maxauthtries: true
ansible_cmdb_report_sysinfo: true
ansible_cmdb_report_tmout: true
ansible_cmdb_report_uname: true
```

Customize HTML overview columns:

```yaml
ansible_cmdb_columns:
  - sysinfo.inventory_hostname
  - sysinfo.hostname
  - sysinfo.ip
  - sysinfo.distribution
  - sysinfo.major_release
  - sysinfo.load
  # - sysinfo.os_family
  - sysinfo.processor_cores
  - sysinfo.memory
  - sysinfo.interfaces
  - tmout.tmout
```

Set custom colors:

```yaml
ansible_cmdb_css_background_color: "#010409"
ansible_cmdb_css_font_color: "#e6edf3"
```

All settings can be found in [defaults/main.yaml](defaults/main.yaml)

## Custom Plugins

Store custom plugins in tasks/reports/custom_reports

## Compliance

This role passes the ansible-lint production profile with zero errors.

# Contribute

We welcome contributions! Please report issues and share your ideas to help us improve.
