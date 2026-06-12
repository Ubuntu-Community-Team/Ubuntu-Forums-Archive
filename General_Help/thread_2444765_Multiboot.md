---
title: "Multiboot"
date: 2020-06-03
forum: General Help
---

### Post by yegnal on 2020-06-03
Going to create a multi boot USB drive and hopefully move the 6 or so bootable thumb drives to one.

Where do I source the .iso files  ?

Can I simply use dd to create .iso 's of each bootable thumb drive I now have, and then migrate those .iso files to whatever multi boot system ?

I'm finding that method creates giant .iso fIles corresponding to the size of each thumb drive being imaged, so I'm thinking there must be a better way.  I have Win10, multiple linux os and linux utilities drives I'd love to get on one thumb drive if possible..

---

### Post by crip720 on 2020-06-04
There are at least a couple of multi boot ISO burners around.  Placing Win 10 on one will probably give most problem unless done from a Windows computer.  Would use new downloaded ISOs if the ones you have are older so you can have updates included.  Here is a google search link that will give you a choice.  [https://www.google.com/search?newwindow=1&client=ubuntu&hs=qAC&channel=fs&sxsrf=ALeKk03501jjqhLvbuOgaBTsjwt7Isad2Q:1591270369659&q=multiboot+iso+usb&spell=1&sa=X&ved=2ahUKEwif4_-IiOjpAhVYhXIEHQTdBD0QBSgAegQIEhAn&biw=1366&bih=670](https://www.google.com/search?newwindow=1&client=ubuntu&hs=qAC&channel=fs&sxsrf=ALeKk03501jjqhLvbuOgaBTsjwt7Isad2Q:1591270369659&q=multiboot+iso+usb&spell=1&sa=X&ved=2ahUKEwif4_-IiOjpAhVYhXIEHQTdBD0QBSgAegQIEhAn&biw=1366&bih=670)

---

### Post by yancek on 2020-06-04
It depends upon how familiar you are with Grub2.  The first link below explains how to put the windows installer on a flash drive to boot.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

You can then copy the Linux iso files directly to that or another partition on the usb drive and boot them directly from Grub2.  There are a number of sites explaining how to do this such as the Ubuntu documentation site at the link below.

 [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

I've used the methods described above to put the windows 10 installer, a  windows 7 recovery install as well as a number of Linux iso files which all boot.  You need some familiarity with Grub2 as you will need to manually create the grub.cfg file and its entries.

---

### Post by kneutron on 2020-06-04
> **yegnal said:**
> 
Can I simply use dd to create .iso 's of each bootable thumb drive I now have, and then migrate those .iso files to whatever multi boot system ?

I'm finding that method creates giant .iso fIles corresponding to the size of each thumb drive being imaged

--Your best bet is probably to re-download the original .iso files (use torrent if at all possible) that were used to create the bootable usb drives.  

--Alternatively, you could mount the usb filesystem and cd to it, then ' time dd if=/dev/zero of=zerofile bs=1M ; /bin/rm -f zerofile ' to zero out the free space in the filesystem.  Then unmount it, and when you image the usb you can pipe it to **gzip** (or store it on an lz4-compressed ZFS filesystem or the like) and it won't take up the full 16GB or whatever size.  

--To write the gzipped image back out to usb, you would need to ' gzip -cd usbimage.dd.gz |dd of=/dev/sdX bs=1M ' - and make damn sure you get the /dev/sdX right, I take no responsibility if you overwrite your boot drive or something.

EDIT: You could also try using **gparted** to shrink the usb filesystem down to the minimum before zeroing it out.

---

### Post by C.S.Cameron on 2020-06-04
If you actually want to run Win 10 off USB, in a MultiBoot you can install "Windows to Go" using Rufus and then do Full installs of Linux OS and Utilities to individual partitions, (just like making a dual boot to HDD, but keep going). 

GRUB2 is also able to boot most downloaded OS/Utility ISO's but persistence is limited to 4GB casper-rw/writable plus 4GB home-rw if multi persistence is required, ('Buntus).

GRUB 2.04, (Ubuntu 20.04) has a hard time booting ISO files, GRUB 2.02, (Ubuntu 18.04) works okay.
Alternatively you can put "rmmod tpm" anywhere above the first menuentry in grub.cfg for GRUB 2.04 and later.
[https://askubuntu.com/questions/1165276/make-full-install-to-usb-able-to-install-ubuntu](https://askubuntu.com/questions/1165276/make-full-install-to-usb-able-to-install-ubuntu)

YUMI BIOS/UEFI also makes great MultiBooters, but with limited persistence.
[https://sourceforge.net/projects/portableapps/files/YUMI-UEFI%20Portable/YUMI-UEFIPortable_0.0.2.2_English.paf.exe/download](https://sourceforge.net/projects/portableapps/files/YUMI-UEFI%20Portable/YUMI-UEFIPortable_0.0.2.2_English.paf.exe/download)

---

