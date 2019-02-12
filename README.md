# Asus Merlin OpenVPN Policy Based Routing Script

### Enable SSH
In System Settings


### Enable JFFS custom scripts and configs
In System Settings

### Set up OpenVPN Client
In my case:
* TUN / UDP
* Create NAT on tunnel: **NO**
* Authentication Settings: Static Key
* Redirect Internet traffic: Policy Rules
* Tunnel Server Endpoint IP: 10.99.100.3
* Tunnel Client Endpoint IP: 10.99.100.4
* Tunnel Interface: tun11


I created two ipset, PBR_DNS and PBR_SRC.
* PBR_DNS: create from dnsmasq `--ipset=/.google.com/PBR_DNS` will add IPs of xxx.google.com to PBR_DNS
* PBR_SRC: pbr by src ip, `ipset add PBR_SRC 192.168.111.111` will let all traffic from 192.168.111.111 routed to VPN


### Custom Scripts & Configs
```
/jffs
  /config              # append dnsmasq config for ipset rules
  /dnsmasq             # custom dnsmasq config files
  /scripts             # openvpn-event script, don't forget to chmod +x

```




