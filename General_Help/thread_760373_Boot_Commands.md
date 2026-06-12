---
title: "Boot Commands"
date: 2008-04-20
forum: General Help
---

### Post by ThomasWii on 2008-04-20
Hi, Me, Windows and Ubuntu have had a lot of fights, and what has happened is that ubuntu installed grub then windows override that and installed mbr, then i got grub back. but when i got it back, ubuntu's boot commands (i must of deleted them some how), so all i need is the commands used to boot ubuntu 7.10. i do know that ubuntu is on hd0,1 if that helps.

Thanks in advance
Thomas

---

### Post by TeoBigusGeekus on 2008-04-20
Please post the results of the command
```
sudo fdisk -l
```
that's -L

and the contents of your menu.lst file
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by ThomasWii on 2008-04-20
Sorry I can't because i cant get in to ubuntu at all, i can get the menu.lst ```
timeout 10
splashimage redhat-8
color light-red/black light-red/light-gray

title Windows at (hd0,0)
root (hd0,0)
chainloader +1

title Ubuntu
root (hd0,1)

```

---

### Post by sandysandy on 2008-04-20
> **ThomasWii said:**
> Sorry I can't because i cant get in to ubuntu at all, i can get the menu.lst 
[/code]

u can boot into ubuntu live Cd or any other live Cd (puppy, damm small linux)and post the output.

regards

---

### Post by TeoBigusGeekus on 2008-04-20
You could probably boot with the live cd and provide the information, but if this is trully your menu.lst, it seem that it is totally buggered.
I am not using 7.10, so I couldn't give you the correct entries for your particular kernel, but if I were you I would go for a complete reinstallation of grub...

---

### Post by ThomasWii on 2008-04-20
how do i install grub again?

thomas

---

### Post by TeoBigusGeekus on 2008-04-20
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
This should cover you...

---

### Post by sandysandy on 2008-04-20
> **ThomasWii said:**
> how do i install grub again?

thomas

have a look at this link on how to re-install grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

alternately u can try super grub disk.

regards

---

### Post by ajgreeny on 2008-04-20
Install explorefs2 in windows assuming you can boot to that and then you can navigate to the ext3 partitions on your machine and find the contents of menu.lst with more certainty.  I think what you posted may be from the live CD itself, though I can't remember if the live CD even has a menu.lst file in the boot/grub folder.

You could always try the contents of my menu.lst file which is basically the same as your setup, and I've edited to get rid of the UUID disk idents.

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```


Good luck

---

