---
title: "xend on edgy - almost there .."
date: 2007-03-09
forum: General Help
---

### Post by denni on 2007-03-09
Have been struggeling to get xen virtualiation to work on edgy without success but at at the moment i am writing this after bootup of xen kernel ( dom0 ).  Did fallow the wiki tutorial at [https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy).   

Get this error messages after xm create edgy-guest.cfg.

> Using config file "/etc/xen/edgy-guest.cfg".
Error: Unable to connect to xend: No such file or directory. Is xend running?
root@hp-ferdavel:/mnt#


the filesystem of the computer is on /dev/hda2 and this is /etc/xen/edgy-guest.cfg

> kernel = "/boot/xen0-linux-2.6.17-6-generic-xen0"
ramdisk = "/boot/xen0-linux-2.6.17-6-generic-xen0.initrd.img"
builder='linux'
memory = 128
name = "edgy-guest"
vcpus = 1
vif = [ 'bridge=xenbr0' ]
disk = [ 'phy:/dev/hdX,hda1,w' ]
root = "/dev/hda1 ro"

anyone got any idea how to came around this???

---

