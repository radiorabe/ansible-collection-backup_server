# Ansible Role - radiorabe.backup_server.backup_server

Install the RaBe backup server component including dependencies, enable and start services.

## Requirements

None.

## Role Variables

| Variable | Default | Description |
| ------------------------------ | ------------------------------------------------------------ | ----------- |
| `backup_server_bindir` | `/usr/local/bin` | Path to install binaries to. |
| `backup_server_btrbk_config_dir` | `/etc/btrbk` | Directory for btrbk configuration. |
| `backup_server_btrbk_url` | `https://raw.githubusercontent.com/digint/btrbk/v0.32.6/btrbk` | URL to btrbk script/version. |
| `backup_server_config_dir` | `/etc/rabe-backup` | Main configuration directory for the backup server. |
| `backup_server_config_files` | *not set* | List of configuration files (not set by default). |
| `backup_server_ovirt_ca_content` | *not set* | oVirt CA certificate content (not set by default). |
| `backup_server_repo_dest` | `/opt/backup` | Destination directory for repository checkouts. |
| `backup_server_repo_tag` | `0.2.0` | Git tag to check out from the repository. |
| `backup_server_repo_url` | `https://github.com/radiorabe/backup.git` | Git repository URL for backup server code. |
| `backup_server_sbindir` | `/usr/local/sbin` | Path to install superuser binaries to. |
| `backup_server_systemd_dir` | `/usr/local/lib/systemd/system` | Directory for systemd unit files. |
| `backup_server_trust_anchor_dir` | `/etc/pki/ca-trust/source/anchors` | Directory for trust anchor (CA) certificates. |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  roles:
    - backup_server
      vars:
        - backup_server_config_files:
            - name: appliances.sh
              content: |-
                GWS=("gw1.local" "gw2.local")
                GW_DIRS=("/dir/1" "/dir/2")
                STREAM="stream1.local"
                STREAM_DIR="/dir/1*"
          backup_server_ovirt_ca_content: |
            -----BEGIN CERTIFICATE-----
            [...]
            -----END CERTIFICATE-----
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
