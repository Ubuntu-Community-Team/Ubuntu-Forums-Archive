---
title: "Cannot block internet access of a sofware with apparmor"
date: 2015-10-07
forum: General Help
---

### Post by Daniyal_Javani on 2015-10-07
Follow [this]("http://askubuntu.com/questions/665777/why-cannot-allow-deny-specific-software-in-ufw-linux") link I do:
```
sudo aa-genprof /usr/lib/x86_64-linux-gnu/ubuntu-geoip-provider
```
And change /etc/apparmor.d/usr.lib.x86_64-linux-gnu.ubuntu-geoip-provider to
```
#include <tunables/global>

/usr/lib/x86_64-linux-gnu/ubuntu-geoip-provider {
  #include <abstractions/base>
  audit deny network,
  audit deny network inet stream,
  deny network inet6 stream,
  deny @{PROC}/[0-9]*/net/if_inet6 r,
  deny @{PROC}/[0-9]*/net/ipv6_route r,
  deny capability net_raw,
  /usr/lib/x86_64-linux-gnu/ubuntu-geoip-provider mr,

}
```
And
```
sudo apparmor_parser -r /etc/apparmor.d/usr.lib.x86_64-linux-gnu.ubuntu-geoip-provider
sudo aa-enforce /etc/apparmor.d/usr.lib.x86_64-linux-gnu.ubuntu-geoip-provider
```
But still ubuntu-geoip-provider use of internet, could you please help me to block this software?

---

