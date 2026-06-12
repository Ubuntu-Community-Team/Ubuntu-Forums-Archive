---
title: "Unable to resolve DNS after ip change in netplan"
date: 2018-12-03
forum: General Help
---

### Post by luca.marinosci@gmail.com on 2018-12-03
Hi everybody,

I'm encountering this tedious issue and I'm honestly having difficulties diagnosing it.

**Pre:**

Fresh Ubuntu Server 18.04 installation
2 net cards, both static IP
[B]
Before changes:[/B]

I was able to dig ubuntu.com or more generally any other dns name without any issue.
[B]
Changes:[/B]

Changed netplan configuration for static card from IP 192.168.0.3 to IP 192.168.0.1, did a * netplan --debug apply* without any issue.

**Problem:**

Dig response (after many seconds, usually) is the follow:

 dig


; <<>> DiG 9.11.3-1ubuntu1.3-Ubuntu <<>>
;; global options: +cmd
;; connection timed out; no servers could be reached
[I]
...and...[/I]

dig ubuntu.com


; <<>> DiG 9.11.3-1ubuntu1.3-Ubuntu <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached



**My ****netplan**** config**

cat /etc/netplan/50-cloud-init.yaml 
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        eno1:
            addresses: 
            - 192.168.0.2/24
            dhcp4: false
            gateway4: 192.168.0.1
            nameservers:
                addresses: [192.168.0.1, 8.8.8.8]
                search: []
        enp2s0:
            addresses:
            - 192.168.1.1/24
            dhcp4: false
            nameservers:
                addresses: []
                search: []
    version: 2

**I can't figure out what's wrong...can anybody help plz?**

---

