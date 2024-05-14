# Ansible Role: DNS

Vlad's DNS Ansible Role

## Requirements

*_N/A_*

## Role Variables

### Cloudflare Dynamic DNS IP Updater

Installs this script  used to update Dynamic DNS (DDNS) service based on Cloudflare!
<https://github.com/K0p1-Git/cloudflare-ddns-updater>

```yml
cloudflare_ddns_updater_enabled: true  # Set to `true` to install ddns updater script
cloudflare_ddns_updater_config:
  auth_email: ""        # The email used to login 'https://dash.cloudflare.com'
  auth_method: "token"  # Set to "global" for Global API Key or "token" for Scoped API Token
  auth_key: ""          # Your API Token or Global API Key
  zone_identifier: ""   # Can be found in the "Overview" tab of your domain
  record_name: ""       # Which record you want to be synced
  ttl: "3600"           # Set the DNS TTL (seconds)
  proxy: false          # Set the proxy to true or false
  sitename: ""          # Title of site "Example Site"
  slackchannel: ""      # Slack Channel #example
  slackuri: ""          # URI for Slack WebHook "https://hooks.slack.com/services/xxxxx"
  discorduri: ""        # URI for Discord WebHook "https://discordapp.com/api/webhooks/xxxxx"
```

### Cloudflare DNS records

```yml
cloudflare_email: xxx  # The email used to login 'https://dash.cloudflare.com'
cloudflare_api_token: xxx  # Your API Token or Global API Key
cloudflare_dns_records:
  - zone: example.com
    type: CNAME
    record: www
    value: example.com
    state: absent
```

## Dependencies

*_N/A_*

## Example Playbook

```yaml
- hosts: all
  become: true
  roles:
      - vladgh.system.dns
```
