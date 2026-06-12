---
title: "No boot entry for slackware 11"
date: 2007-07-09
forum: General Help
---

### Post by Thyme on 2007-07-09
I've installed Slackware 11 on a second partition on my hdd. Ubuntu currently has a few entries in grub which I can choose to boot from but after installing Slackware, the Slackware entry doesn't appear in the grub menu.

I've installed it twice and on each occasion have selected or deselected the option to add a lilo entry or something like that...I can't remember to be honest with you.

So my question is...how do I add a boot entry for Slackware 11 to my grub boot loader?

*(Its installed but I can't seem to see/boot it)*

Thanks

---

### Post by Kodfish on 2007-07-09
post the results of 'sudo fdisk -l' please

---

### Post by Thyme on 2007-07-09
Wow Kodfish, thanks for the quick help... I'm currently at work so I'll have wait till I get home...

However, I think I may have already done it and saw the Slackware partition listed their... What's the next step - if I may politely ask?

---

### Post by Kodfish on 2007-07-09
depending on what partition it is, you edit /boot/grub/menu.lst, unless you want to use lilo, slackware's (imho bad) bootloader. here is a quick breakdown. in grub syntax, sda1 would be (hd0,0). sdA meaning 0, and the 1 meanong 0. (grub counts from 0 up). assuming your partitions are sane, you will want something like ```
title Slackware 11 Linux
root (hd1,0)
kernel /boot/{whatever slackware names their kernels}

```
though that is most likely not the case. slackware probly wants to mess everything up. after doing the fdisk -l, you can see where everything is. after you find the /boot partition, you'd want to check the kernel names. and then try to do what i said just earlier in this post. if there is no /boot, or it's configured differently, it can be tricky. you might even want to copy over the correct kernel to your ubuntu's /boot and boot from that partition. it's hard to say exactly what to do, since i don't have all the data, but thats pretty much the procedure. good luck.

---

### Post by Thyme on 2007-07-09
Thanks, much appreciated.

Seems like nitty-gritty stuff so I'll try it at home and post back when I'm successful or not at it...

---

### Post by Thyme on 2007-07-09
Need help! This the output of "fdisk -l"


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         183        6614    51665040   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda3            6615        9355    22017082+  83  Linux
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

**Notice the "Partition table entries are not in disk order"

my menu.lst:


title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Slackware 11 Linux
root            (hd0,1)
kernel          /boot/vmlinuz root=/dev/sda3 ro
quiet
savedefault
boot


** I noticed that  ubuntu uses (hd0,0) so I also used that format... When I tried to boot the slackware parition then it says that the partiion cannot be booted with error E17...

---

### Post by Thyme on 2007-07-10
Can anybody please help me, I really don't know what to do. How to I order my partitions properly and how can I add slackware to my grub menu.

Sorry for "nagging" but I don't feel great when I have 20 gigs of free space plus I can't even use slackware. I have googled but I can't seem to find a solution relative to my (minimal) Linux experience...

Thanks

---

### Post by confused57 on 2007-07-10
> **Thyme said:**
> Can anybody please help me, I really don't know what to do. How to I order my partitions properly and how can I add slackware to my grub menu.

Sorry for "nagging" but I don't feel great when I have 20 gigs of free space plus I can't even use slackware. I have googled but I can't seem to find a solution relative to my (minimal) Linux experience...

Thanks
Try using grub's CLI to investigate your boot entries for slackware:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer)
scroll down to the section "find vmlinuz"

I don't have much time to help you at the moment, but I was able to boot Zenwalk(which uses lilo), using this method.

Added:  Here's the entry I had to use to boot Zenwalk:
root (hd0,1)
kernel /boot/vmlinuz-2.6.20 ro
boot

---

### Post by Thyme on 2007-07-10
Thanks alot confused57, it is much appreciated...

I'll give this method a go and so how it turns out.

Cheers

---

