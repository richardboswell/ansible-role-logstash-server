# ansible-role-logstash-server

Ansible playbook to automate installing and maintaining logstash as containers.

## Requirements

This role currently requires a working VMware Photon server with enabled
Docker environment.

This role also has a dependency on the
[Chaperone](https://github.com/vmware/chaperone) project. In particular, this
role requires that an external source (e.g., the playbook) define the following
variable (the default expectation is supplied, but can be any valid Docker
version):

```yaml
# The Docker API version to use for manipulating the containers.
docker_api_version: 1.18
```

## Role Variables

```yaml
# Container memory limit. Use 512MB, type string, or 0 for unlimited.
memory_limit: 0MB

# Where to place temporary build artifacts when building the container.
logstash_docker_build: /tmp/logstash

# Directories (volumes) to map to /config-dir in the container.
# Note, not currently used, but planned for future use.
logstash_mapped_dir:

# The Docker image to use to start containers.
logstash_docker_image: openedge/logstash-server

# The elasticsearch cluster to link to.
elasticsearch_cluster_name: default_clustername

# TCP port that logstash listen on (as syslog) within the container.
logstash_server_port: 514

# TCP container (public) port to map to the container internal logstash port.
logstash_container_port: 514
```

## Example playbook

```
---
- hosts: logstash-servers
  sudo: True
  roles:
    - logstash
  vars:
    - ... forthcoming
```

# License and Copyright
 
Copyright 2015 VMware, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

