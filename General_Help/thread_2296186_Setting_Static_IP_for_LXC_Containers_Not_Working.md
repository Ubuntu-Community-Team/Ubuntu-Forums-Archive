---
title: "Setting Static IP for LXC Containers Not Working"
date: 2015-09-24
forum: General Help
---

### Post by JengaBlocks on 2015-09-24
Running into a problem assigning static IP addresses to my LXC containers.

The first container is always set to 10.0.3.69 and I have no idea why.

I can get two other containers set to their specified addresses in my conf file.

I have setup things like so:

**lxc-net**
LXC_DHCP_CONFILE=/etc/lxc/dnsmasq.conf


**/etc/lxc/dnsmasq.conf**
dhcp-hostsfile=/etc/lxc/dnsmasq-hosts.conf

**/etc/lxc/dnsmasq-hosts.conf**
dhcp-host=Container1,10.0.3.3
dhcp-host=Container2,10.0.3.4
dhcp-host=Container3,10.0.3.5

I then reboot the system and startup all the containers as so:
lxc-start -n Container1 -d
lxc-start -n Container2 -d
lxc-start -n Container3 -d

Upon doing a listing of all containers I get:
lxc-ls -f

NAME          STATE         IPV4            IPV6              AUTOSTART
------------------------------------------------------------------------------------
Container1  RUNNING    10.0.3.69       -                       NO
Container2  RUNNING    10.0.3.4         -                       NO
Container3  RUNNING    10.0.3.5         -                       NO

As you can see, the first container is assigned 10.0.3.69 and I have no idea why.
The other containers are set correctly.

Any ideas how to fix this?

---

