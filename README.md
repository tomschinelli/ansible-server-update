# ansible-server-management
Collection of useful tasks including:
- centralized user management
- server upgrades
- (ToDo) standard software like monitoring requirements

## Run Playbook

Run complete setup:
```shell
ansible-playbook site.yml -i production
```

Create users only:
```shell
ansible-playbook site.yml --tags user -i production
```


## Configuration
### Users :busts_in_silhouette:
By default, a user `admin` is created with your default ssh public key. 
You can set up users inside `host_vars/{hostname}.yml` or `group_vars/{group_name}.yml`:

```yaml
# example: ./group_vars/all.yml
users:
  - name: tom
    publicKeyPath: ~/.ssh/id_rsa.pub
```

### Upgrades :arrow_up:

#### Security patches only (WIP)
Set `ev_security_only=yes` inside `group_vars/all.yml` or run with the option `-e ev_security_only=yes`