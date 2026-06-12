---
title: "OpenVPN client working from CLI, but fails using the deamon"
date: 2024-04-07
forum: General Help
---

### Post by anderstn on 2024-04-07
Hi

I have made an OpenVPN client config that works fine when i run it manually as root, however when i try to run it as a deamon it fails and there is no sign in the logs of what is happening.

Here is the configuration (some things removed obviusly)
```

clientdev tun
remote "REMOVED FOR SECURITY REASONS" 41185
resolv-retry infinite
nobind
persist-key
persist-tun
auth-nocache
verb 3
explicit-exit-notify 5
push-peer-info
setenv UV_IPV6 yes
remote-cert-tls server
cipher AES-256-CBC
comp-lzo no
proto udp
auth SHA512
<ca>
-----BEGIN CERTIFICATE-----
REMOVED FOR SECURITY REASONS
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
REMOVED FOR SECURITY REASONS
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
REMOVED FOR SECURITY REASONS
-----END PRIVATE KEY-----
</key>
<tls-crypt>
-----BEGIN OpenVPN Static key V1-----
REMOVED FOR SECURITY REASONS
-----END OpenVPN Static key V1-----
</tls-crypt>

```

The command I use to run it manually is:
sudo openvpn client.ovpn
Trying to run it as a demon i use:
sudo systemctl start [email]openvpn@client.ovpn[/email]

The absolute path to the config file is /etc/openvpn/client/client.ovpn

Obviusly I'm doing something wrong, but per the tutorial published by ubuntu, [https://ubuntu.com/server/docs/service-openvpn](https://ubuntu.com/server/docs/service-openvpn), I can't figure out what my mistake is.

---

### Post by anderstn on 2024-04-07
Apparently the config needs to be in /etc/openvpn and have a conf file extension. This solved the problem

---

