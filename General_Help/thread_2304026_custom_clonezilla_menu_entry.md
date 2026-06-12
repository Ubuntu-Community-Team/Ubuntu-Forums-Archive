---
title: "custom clonezilla menu entry"
date: 2015-11-23
forum: General Help
---

### Post by thenamelessthing on 2015-11-23
Hi, I try to build an semi-automatic entry in my clonezilla usb stick.

label Clonezilla live, ::: Restore :::
  MENU LABEL Clonezilla live, ::: Restore :::
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live username=user config quiet noswap locales=en_US.UTF-8 -k NONE ocs_prerun="dhclient -v eth0" ocs_prerun1="sleep 2" ocs_prerun2="mount -t cifs -o user=clonezilla,domain=MYDOMAIN,password=MYPASS 10.26.0.146:/images /home/partimag" ocs_prerun3=sleep2" ocs_live_batch=no ocs_live_run="ocs-sr -g auto -e1 auto -e2 -c -r -j2 -p true restoredisk ask_user ask_user"



**But I obtain the following error: **

/bin/sh can't access tty; job control turned off
(initramfs) mount: mounting aufs on /root/ failed: no such device
mount aufs on root failed with option -o noatime,,dirs=/live/orverlay/=rw://filesystem.squashfs/=rr=wh
modprobe: module ehci-orion not found in modules.dep



Anybody can help me??

---

