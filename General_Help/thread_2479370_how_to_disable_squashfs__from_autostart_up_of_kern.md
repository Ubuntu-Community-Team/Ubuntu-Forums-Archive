---
title: "how to disable squashfs  from autostart up of kernel modue (ubuntu 20)"
date: 2022-09-22
forum: General Help
---

### Post by ncgjiju138 on 2022-09-22
Hi,

       I  need to disable the  squashfs  from  autoloading -
a) When we  run the command -> modprobe squashfs , we  get  
name : squashfs
filename : (builtin)
author: Phillip Lougher
alias : fs-squashfs
b) when we  run the following it is empty, the driver is not loaded.
modprobe -n -v squashfs | grep -E '(squashfs|install)'
Ans : Empty

lsmod | grep squashfs      
Ans: Empty       <<--- Not loaded 

cat /proc/self/mounts | grep -i squash
Ans: Empty                   

cat /proc/modules / | grep squash
Ans:  Empty              <<--- Not loaded 

Checking done :
a)  in /etc/moduled-load.d, kept a  backup copy of modules.conf  and  removed the file.
b)  in /etc/modprobe.d,  added the squashfs.conf with "install squashfs  bin/true"
c)  in /etc/moduled-load.d, checked the blacklist also no squashfs

rebooted the machine ,it  still  load squashfs as inbuilt. Please help as I tried all the  tricks still unbale to remove as inbuilt. Thank u for help  in advance.regards,George

---

### Post by MAFoElffen on 2022-09-24
Not sure about disabling squashfs at kernel level. I know in college, when we built kernels and not using instramfs, we had to disable it in the kernel, then tell Grub2 how to boot it. I think basically, it might be the same concepts. I could be wrong.

We did that for RHEL. I found this for Slackware. The concepts seem to be how I remember that. 
[https://firasuke.github.io/DOTSLASHLINUX/post/booting-the-linux-kernel-without-an-initrd-initramfs/](https://firasuke.github.io/DOTSLASHLINUX/post/booting-the-linux-kernel-without-an-initrd-initramfs/)

Sorry if it is not the same as for squashfs, but maybe it might give you ideas(?)

---

