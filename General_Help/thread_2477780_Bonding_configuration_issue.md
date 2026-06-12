---
title: "Bonding configuration issue"
date: 2022-08-07
forum: General Help
---

### Post by pradeep8985 on 2022-08-07
[COLOR=#232629][FONT=-apple-system][FONT=var(--theme-post-body-font-family)][FONT=inherit]I have enabled multiple nic bonding with vlans on my ubuntu 22.04 machine with 2 interfaces each. One of the interfaces is connected to Switch 1 and the other one goes to Switch2. Here is what happening, when i bring down the port connected to switch 1 , i am unable to ping the machine. Ideally server  should automatically be reachable via the switch 2 port, but its not. Network guy says he is not able to learn the MAC from the other interface and there is no other config needed to be done on switch layer when its active-backup bonding, which seems to be true.[/FONT]
[FONT=inherit]Here is what my bonding looks like in netplan configuration file. Is there a problem in the netplan configuration file? If so, please help to correct.[/FONT]
```
# This is the network config written by 'subiquity'network:
  version: 2
  ethernets:
    eno12399np0:
      dhcp4: no
    eno12409np1:
      dhcp4: no
    eno8303:
      dhcp4: no
    eno8403:
      dhcp4: no
    enp177s0f0np0:
      dhcp4: no
    enp177s0f1np1:
      dhcp4: no
  bonds:
    bond0:
      dhcp4: no
      interfaces: [enp177s0f0np0, eno12409np1]
      parameters:
        mode: active-backup
        primary: enp177s0f0np0
    bond1:
      dhcp4: no
      interfaces: [enp177s0f1np1, eno12399np0]
      addresses: [192.168.1.2/27]
      parameters:
        mode: active-backup
        primary: enp177s0f1np1
  vlans:
    vlan209:
      id: 209
      link: bond0
      dhcp4: no
      addresses: [100.100.50.75/27]
      gateway4: 100.100.50.65
      nameservers:
        addresses:
[FONT=var(--ff-mono)]          - 8.8.8.8[/FONT]
```[/FONT][/FONT][/COLOR][FONT=-apple-system][FONT=var(--theme-post-body-font-family)]


[/FONT]
[/FONT][/COLOR]

---

