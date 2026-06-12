---
title: "Hacking VM Guest Access to Host Samba Share; Samba Restarts"
date: 2019-04-03
forum: General Help
---

### Post by ebsf on 2019-04-03
No posts on point, so a reference note for others.

Ubuntu 16.04 host, Windows 7 guest via VMware Workstation.  Samba configured on host for LAN and guest VM access.

The problem I had was having to restart Samba from terminal for the VM to see the Samba shares.  The service was running and LAN access worked, but not VM guest access unless I restarted Samba.  Other notes suggested restarting with some tweaks of /etc/init.d but these weren't apt.  The fix, though, is simply to load the host virtual network adapter (here, vmnet8) at boot by adding the following line to /etc/network/interfaces:

```
auto vmnet8
```

Other notes regarding the configuration:

Samba is far faster than the native VMware host file access ("Shared Folders") configuration.  Key smb.conf settings are:

```
    interfaces = lo [local interface names] vmnet8
    bind interfaces only = Yes
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=131072 SO_SNDBUF=131072
```

Open the host's firewall to allow connections from the guest adapter's IP.

In VMware Workstation, turn off host file access ("Shared Folders") in Virtual Machine Settings.

HTH

---

