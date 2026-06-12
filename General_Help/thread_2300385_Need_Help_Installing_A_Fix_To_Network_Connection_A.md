---
title: "Need Help Installing A Fix To Network Connection Applet"
date: 2015-10-25
forum: General Help
---

### Post by jooge on 2015-10-25
I am trying to install a VPN with OpenVPN but the instructions given tell me to import the .ovpn file with the "Import" button on the network-conection applet. Since the button has been removed in Ubuntu 14.04 (thats what I run) I had to find a workaround. I found this but am completely lost as to how to, and where to install the fixes/upgrades.


The fix is from here: [https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1294899](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1294899) - Comment #31: [https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1294899/comments/31](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1294899/comments/31) - Everyone that commented after that said that they were now able to add the .ovpn file after adding the upgrade.

Upgrade was from here: [https://launchpad.net/ubuntu/+source/network-manager-applet/0.9.8.8-0ubuntu4.1](https://launchpad.net/ubuntu/+source/network-manager-applet/0.9.8.8-0ubuntu4.1) - I downloaded both the tar.gz file and the tar.xz files. I dont know how or where to install these types archives in order for the fix to work..

Please help

---

### Post by bapoumba on 2015-10-26
From the bug report the package is network-manager-gnome. Current Trusty version is 0.9.8.8-0ubuntu4.4. Is your system updated/upgraded ? 
Please check which package you are currently running :
```
apt-cache policy network-manager-gnome
```

---

