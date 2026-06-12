---
title: "cisco vpn client help needed!"
date: 2005-06-01
forum: General Help
---

### Post by aliased on 2005-06-01
hey guys, heres a noobish question for u.
ive installed the latest cisco vpn client for linux and have everything running. however, i have not been able to figure out how to start the vpn service during bootup. ive made sure to allow for this during installation, but everytime i want to connect i still have to input beforehand: "sudo /etc/init.d/vpn_client start"

ive also looked into the [Ubuntu bootup howto](http:/www.ubuntulinux.org/wiki/ubuntubootuphowto) and followed the "installing custom init-scripts" guidelines... and i get the following error:

root@noneleft:/home/reset # sudo chmod +x /etc/init.d/vpnclient_init
root@noneleft:/home/reset # sudo update-rc.d vpnclient_init start 51 S .
update-rc.d: warning: /etc/rc3.d/S85vpnclient_init is not a link to ../init.d/vpnclient_init
update-rc.d: warning: /etc/rc4.d/S85vpnclient_init is not a link to ../init.d/vpnclient_init
update-rc.d: warning: /etc/rc5.d/S85vpnclient_init is not a link to ../init.d/vpnclient_init
 System startup links for /etc/init.d/vpnclient_init already exist.

anyone have any idea on what is going on? and... how should i go about resolving this issue. your help would be appreciated. thanks

---

