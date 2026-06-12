---
title: "Ubuntu 8.04 and GRUB"
date: 2008-04-25
forum: General Help
---

### Post by alphabetical on 2008-04-25
Hello.  

I having wiped my HD after a most unfortunate mistake am setting up my HD partitions and bootloader the way I want them.  

Here's the plan

GRUB installed on a "standalone" partition
Windows XP
Ubuntu 8.04 

Currently I have the HD formatted (all partitions) and Ubuntu installed.  I have been following this guide to setup GRUB.
 [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

I am to step 6 and got lost.  The guide points to this page on "Config file boot entry" and how to do it.  I don't understand

[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

Could someone look over the instructions and help me to figure out how to complete this step?  

Thank you,
Alphabet

EDIT: 

Here's a copy of my menu.lst

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4d386bf1-dbbe-4b24-9949-9d67b7c6f891 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4d386bf1-dbbe-4b24-9949-9d67b7c6f891 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIS

---

