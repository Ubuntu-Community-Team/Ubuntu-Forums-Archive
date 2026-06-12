---
title: "Network Connection Lost - Multiple NIC Virtualization Server"
date: 2020-04-13
forum: General Help
---

### Post by w4ffl32 on 2020-04-13
I am running Ubuntu Server 18.04 and libvirt. I manage the VM's with virtmanager.  
The computer has 5 nic's:
[LIST]
[*]3x 1Gb
[*]2x 10Gb
[/LIST]
The hypervisor os connects to the network with dhcp on one of the 1Gb connections.
I have the other interfaces configured to not automatically connect, and not available to all users. I have two vm's, each with one virtual nic - macvtap - passthrough - (Unique Not autoconnected NIC).

At boot up, everything works great. Each machine is assigned its own IP. I can connect to each machine from the network. Each of the machines are connected to the same network and VLAN (for now). Between 4 and 6 hours of uptime, I lose connection to all of the machines. The link light on the switch is solid, indicating no activity.

Is this a bug, or a configuration issue?

Thank you.

---

### Post by QIII on 2020-04-13
Hello!

Do your NICs have a low-power configuration that shuts them down after some period of inactivity?

---

### Post by w4ffl32 on 2020-04-14
The gigabit NICs are all Realtek RTL8111GR. Prior to ubuntu 18.04, I was running Debian 9. I did not experience any inactivty shutdowns, nor did I change the hardware.
I am not seeing any low power mode in network manager. Where else would I look?

---

