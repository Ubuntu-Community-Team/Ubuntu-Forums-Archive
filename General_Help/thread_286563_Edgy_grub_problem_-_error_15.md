---
title: "Edgy grub problem - error 15"
date: 2006-10-27
forum: General Help
---

### Post by m.musashi on 2006-10-27
I was hesitant to upgrade my dapper install so I installed edgy to a separate HD and had grub also install to that drive (sdb). When I rebooted from sdb, grub loads but both the edgy install and my dapper install do not boot. Instead I get an error 15 message. If I reboot from sda HD I am able to load dapper just fine as before but not edgy (of course it's not in the menu.lst on that HD - maybe I should add it). Can you have grub on two HDs? Here is the menu.lst from the edgy install
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.15-27-686 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.15-27-686 (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda6 ro single 
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.15-27-386 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda6 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
Any idea why this isn't working? sdb6 is the location of the edgy install.

Thanks for any help you can offer.

---

### Post by m.musashi on 2006-10-28
Okay, I sort of fixed this myself. I added the entries into the original grub to boot edgy and it worked fine. It seems that for some reason the new grub install on the second HD didn't want to work. When I installed edgy I didn't want my grub on sda to be overwritten since if things didn't work I would still be able to boot dapper.

However, now when I make changes to edgy (like installing a new kernel) it writes the changes to the grub menu on sdb. Then I have to go into the old grub menu and add the change so that the next time I boot it will be there.

How do I tell edgy to disregard the grub on sdb and just use the sda grub? Is there a way to make the sdb grub work? If anything happens to one HD, it's nice to know I can always use the other one.

---

### Post by Herman on 2006-10-28
Hello m.musashi,
Sure you can have Grub on as many hard disk's MBRs as you like.  It certianly does no harm and possibly some good to use both disk's MBR's.
> If I reboot from sda HD I am able to load dapper just fine as before but not edgy (of course it's not in the menu.lst on that HD - maybe I should add it). You can do that (add it) in several different ways.
My favorite way is to add an entry in my first hard disk's Grub something like this, 
```
title                Ubuntu Edgy Eft
configfile       (hd1,5)/boot/grub/menu.lst
```That should bring up your Edgy Eft grub menu if you select that from your Dapper Drake grub menu in your first hard disk.

Another way to do the same thing is to chainload your second hard disk's MBR this way,
```
root           (hd1)
chainloader +1
boot
``` or, you can press your F8 or FR12 key at the right time during boot-up to select your second hard disk.


Regards, Herman :D

---

### Post by m.musashi on 2006-10-28
Thanks for the info. I managed to get my dapper grub to boot edgy but I can't get the edgy grub to boot anything. My first post contained the contents of the edgy grub. It is exactly as the edgy install set it up, but on first boot I got the error 15 message. Any time I try to boot the edgy grub it loads and shows the menu but if I sellect an entry to boot I get the error 15 (I think it said "disk error - no such file system" or something like that.

Thanks.

---

### Post by Herman on 2006-10-28
Try pressing 'c' from your grub menu for a grub [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and see if you can find out how to boot it that way first. Take notes while you do that, then edit its menu.lst with the required changes. :D

Regards, Herman :D

---

