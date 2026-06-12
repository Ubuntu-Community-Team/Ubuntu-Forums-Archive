---
title: "How do I get grub/Ubuntu back?"
date: 2005-09-20
forum: General Help
---

### Post by abandoned_hussam on 2005-09-20
I have two hard disks. I have windows installed on hda1 . I have Ubuntu installed on the other hard disk ( hdb1 is the swap and hdb2 is / ).
This is the relevant part from my /etc/fstab: 
```

/dev/hdb2   /   ext3	defaults,errors=remount-ro 0	   1
/dev/hdb1	 none	 swap sw	  0	 0
/dev/hda1    /media/windows  ntfs    umask=0222	0	0
```
This is the rellevant part from menu.lst:
 ```
title		Ubuntu, kernel 2.6.12-8-686 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-8-686 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-8-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-8-686 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-8-686 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.12-8-686
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title  Microsoft Windows XP Professional
root  (hd0,0)
savedefault
makeactive
chainloader +1

``` 

I need to reinstall windows on the first hard disk since it's busted. 
I'm on breezy. I don't have a breezy CD but I still have the old hoary cd. I also have a Mepis Live cd.
Can somebody give me some instructions on how to repair grub after I reinstall windows this weekend? If possible, can you make the instructions relevant to my case ( in terms of hd(0,0) etc...)

---

### Post by aysiu on 2005-09-20
Have you seen this?

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by abandoned_hussam on 2005-09-20
[QUOTE=aysiu]Have you seen this?

[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")[/QUOTE]
 Ok thanks, I'm reading it now. 
Will this work if I have breezy but I use hoary CD?
Also, I still don't get the numbering hd(0,0), hd(1,1). 
All I know is that on my PC hda1 has xp that came preinstalled with the computer. On the second hard disk, hdb1 is swap and hdb2 is /.
Also which is safer, the Ubuntu CD method or Mepis Live CD method?

Edit:. I'd rather use the Live CD if I understand what I should do.

---

