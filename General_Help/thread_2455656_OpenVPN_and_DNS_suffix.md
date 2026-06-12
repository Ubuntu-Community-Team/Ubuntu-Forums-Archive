---
title: "OpenVPN and DNS suffix"
date: 2020-12-24
forum: General Help
---

### Post by geronimo350 on 2020-12-24
Hi,


my current openvpn configuration on client side successfully establishes connection and works fine (with openvpn --config cmd), but I'm unable to properly set DNS suffix in order to use short names for IP resolution.


In my openvpn configuration I have set following (with dummy ip):
```

...
script-security 2
dhcp-option DNS 1.1.1.1
dhcp-option DOMAIN home.local
dhcp-option DOMAIN-ROUTE .
up /etc/openvpn/update-systemd-resolved
down /etc/openvpn/update-systemd-resolved

```


When I establish openvpn connection, it properly sets tun0 interface:
```

...
Link 22 (tun0)
      Current Scopes: DNS       
DefaultRoute setting: yes       
       LLMNR setting: yes       
MulticastDNS setting: no        
  DNSOverTLS setting: no        
      DNSSEC setting: no        
    DNSSEC supported: no        
  Current DNS Server: 1.1.1.1
         DNS Servers: 1.1.1.1  
                      1.1.1.2  
          DNS Domain: home.local
...

```


and also ads the domain in resolv.conf file:
```

nameserver 1.1.2.1      # 1st ISP DNS
nameserver 1.1.2.2      # 2nd ISP DNS
nameserver 10.1.2.5    # 1st custom DNS
# Too many DNS servers configured, the following entries may be ignored.
nameserver 10.1.1.2    # 2nd custom DNS
search home.local        # Domain defined in openvpn config file

```


In order to use ping cmd for shortname and FQDN resolution, I have updated nsswitch.conf file by moving "dns" in front of "[NOTFOUND=return]". But issue with nslookup still remand (which is logical, since it doesn't use nsswitch.conf).


Now my problem is with resolve.conf file. Even though "search home.local" parameter is set, it's set as the last line in file. When I hardcode it to be a first line, the nslookup cmd works fine. But when it's defined as last line, nslookup cannot resolve shortnames. 


Is there some way that I can set "search home.local" to be the first line in resolve.conf through openvpn config (I'd like to avoid any extra scripting and hardcoding)?


P.S. When using Ubuntu GUI for setting it's VPN everything worked fine after setting nmcli:
    nmcli c modify home ipv4.dns-search 'home.local'
    
    Only difference between VPN gui and openvpn cmd, when connected, (as far as I noticed) is in the DNS set in "systemd-resolve --status":
    VPN GUI:[INDENT]DNS Domain: ~.[/INDENT]
[INDENT=3]  home.local[/INDENT]

    OpenVPN cmd:[INDENT]DNS Domain: home.local[/INDENT]
[INDENT=3]  ~.[/INDENT]

---

