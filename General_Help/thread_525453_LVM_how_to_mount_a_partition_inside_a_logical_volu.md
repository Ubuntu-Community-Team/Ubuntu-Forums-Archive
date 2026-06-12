---
title: "LVM: how to mount a partition inside a logical volume?"
date: 2007-08-14
forum: General Help
---

### Post by woorzel on 2007-08-14
Hello,

I have a question about mounting a partition that resides within an logical volume.
Here's what I'm doing:

For XEN virtual machines each time I create a new virtual server I create a  corresponding logical volume for it. I then pass this device (something like /dev/volgroupxen/lvsrv01) to the virt-install XEN installer.
I partition this up like it was a regular disk device and it works just great.

now my question: how do I mount a filesystem that is contained in this logical volume from the XEN host server? (say for troubleshooting or other reasons).
I can create a device file with mknod for the logical volume, but that points to the whole thing (all partitions). I cannot seem to figure out how to access a subpartition directly.

example: /dev/volgroupxen/lvsrv01 is partitioned up in /dev/xvda1 (root) and /dev/xvda2 (swap). 
note that the xvda1/2 names are as seen by the XEN virtual machine.

If I run fdisk on /dev/volgroupxen/lvsrv01 it will show something like this:

/dev/volgroupxen/lvsrv011   *           1         652     5237158+  83  Linux
/dev/volgroupxen/lvsrv012             653         783     1052257+  82  Linux swap / Solaris

I haven't been able to create a device file with mknod that would point to 
**/dev/volgroupxen/lvsrv011** and not just 
/dev/volgroupxen/lvsrv01. Therefore I cannot access this filesystem, unless I boot the virtual machine. Obviously this is not ideal...

does anyone have an idea how to do this?

thanks a lot

---

### Post by daserzw on 2008-04-28
Have a look here:

[http://www.novell.com/coolsolutions/tip/19568.html](http://www.novell.com/coolsolutions/tip/19568.html)

simply put you have to create the device nodes for the partitions inside the logical volume, then you can mount them.

greetings
davide

---

