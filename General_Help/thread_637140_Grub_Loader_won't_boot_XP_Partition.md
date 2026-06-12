---
title: "Grub Loader won't boot XP Partition"
date: 2007-12-10
forum: General Help
---

### Post by Rostam on 2007-12-10
Hi. I recently installed Ubuntu on my laptop. I have been trying to get Grub to load my windows xp x64 but it won't work. My windows partition is sda5. I am pretty new to Ubuntu, but I love it so far. I just want to dual boot windows. 

My menu.lst has no entry for windows. I tried some suggestions from other forums but none of them seemed to match my partition.

My Menu.lst:

> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=165d50e0-20b8-4b5c-a1de-34d7fded7cd0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=165d50e0-20b8-4b5c-a1de-34d7fded7cd0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


A view of my partitions (sda5 is where XP is):
[IMG]http://farm3.static.flickr.com/2286/2101155007_40b2b29a66.jpg[/IMG]

---

### Post by LaRoza on 2007-12-10
Add this to the end of /boot/grub/menu.lst:

```

title           Windows
root            (hd0,4)
makeactive
chainloader     +1


```

---

### Post by Rostam on 2007-12-11
I tried that and it didn't work. Sorry. 

I did have Vista on my first partition and I put ubuntu over it.

---

### Post by r-mo on 2007-12-11
OK, there is probably an easier way of doing things than this but...

You could try repairing the XP bootloader
[LIST]
[*]Boot from the Windows XP CDROM in to the “Recovery” prompt.
[*]Log in with your administrator password
[*]bootcfg /rebuild
[*]fixboot
[*]fixmbr
[/LIST]

Then check you can boot into Windows XP, Grub should be gone so no way to boot into Ubuntu, obviously you don't want this!! 

So follow the guide here [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)
to reinstall grub.

HTH

---

