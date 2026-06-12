---
title: "Adding Ubuntu 7.04 to Grub...How?"
date: 2007-05-21
forum: General Help
---

### Post by BC2210 on 2007-05-21
Hey,

I just installed Ubuntu FF 7.04 along side Fedora Core 6 and XP.  XP and Fedora were already listed in my grub menu, and I guess its LILO that comes with Ubuntu?  It took over grub and started booting only Ubuntu so I reinstalled grub and now grub works but it only boots the other two! :) 

I know how to edit the grub menu, but what should I actually type in the grub.conf?  

I think root for Ubuntu is in sda (0,5)...

Thanks! :)

---

### Post by confused57 on 2007-05-21
> **BC2210 said:**
> Hey,

I just installed Ubuntu FF 7.04 along side Fedora Core 6 and XP.  XP and Fedora were already listed in my grub menu, and I guess its LILO that comes with Ubuntu?  It took over grub and started booting only Ubuntu so I reinstalled grub and now grub works but it only boots the other two! :) 

I know how to edit the grub menu, but what should I actually type in the grub.conf?  

I think root for Ubuntu is in sda (0,5)...

Thanks! :)
Ubuntu uses grub...you might be able to boot Ubuntu using configfile:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Maybe something like this:
```
title        Ubuntu Feisty on /dev/sda6
savedefault
configfile   (hd0,5)/boot/grub/menu.lst
```

---

### Post by BC2210 on 2007-05-21
That worked!  Thanks alot, I had to edit the partition numbers of course but everythings good...I appreciate it! :)

---

### Post by ghell on 2007-05-21
Ubuntu's seems more stable than Fedora's GRUB as far as I can tell too, I couldn't get memtest to work under fedora unless I booted it from the DVD (said something about not enough space to load it) but on Ubuntu it is even enabled by default!

Watch out for kernel updates though, fedora updates its kernel pretty frequently and you will need to edit your ubuntu menu.lst to match the version numbers.

EDIT: or use that configfile thing I suppose, I have never used it so I don't know much about it :)

---

