---
title: "Grub error 17 after resizing partition"
date: 2007-03-11
forum: General Help
---

### Post by fearpi on 2007-03-11
I dual boot WinXP and Ubuntu Edgy. I just decreased the size of the NTFS partition and increased the size of the linux partition. Now when I boot, I get Grub error 17. How should I fix this? Probably by modifying something in /boot/grub/?

---

### Post by puccaso on 2007-03-11
ok
you need to try and remember ur HD config before u did the resize

which partition was active? (enabled to boot)

you may need have to play around with activating or deactivating some of ur partitions
there is a barrier on hard drives, that stop partitions from being booted if they active after a certain size. 

also 
if u can
send us 
ur harddrive config before
like just the sizes etc
and 
ur hd config now
and we'll asess further

---

### Post by fearpi on 2007-03-11
I ran the gnome partition editor and made a minor change. When I applied the changes, my issues were resolved. Thanks anyway.

---

### Post by puccaso on 2007-03-11
can u tell us what u did 
how did u solv it

so that we can fix it ourselves in the future

---

### Post by fearpi on 2007-03-11
While running from the live CD, I simply resized one of the partitions, clicked Apply, and then put it back to its original size and clicked Apply. The partition editor seems to handle all of the grub configuration for me.

---

### Post by bill57785 on 2007-03-12
My partition containing Linux ran out of room while I was using Ubuntu. Then it wouldn't let me delete anything or run any programs. It froze so I restarted. When I went to login, it would just reload the login screen. Then I switched to XP and took some space from the Windows partition in the Ubuntu partition using Norton PartitionMagic. Now I get a GRUB error 17 message when I boot. I don't have my LiveCD with me and all I have to use is this stupid PSP (which is hard to type on). What do you suggest?

---

### Post by bill57785 on 2007-03-12
Sorry for the bump but I need this fixed badly.

---

### Post by fearpi on 2007-03-12
Unfortunately, I don't have any recommendations other than to get your hands on a live CD somehow. Sorry.

---

### Post by confused57 on 2007-03-13
> **bill57785 said:**
> My partition containing Linux ran out of room while I was using Ubuntu. Then it wouldn't let me delete anything or run any programs. It froze so I restarted. When I went to login, it would just reload the login screen. Then I switched to XP and took some space from the Windows partition in the Ubuntu partition using Norton PartitionMagic. Now I get a GRUB error 17 message when I boot. I don't have my LiveCD with me and all I have to use is this stupid PSP (which is hard to type on). What do you suggest?
If you get a grub menu at startup, you could experiment with various combinations for your root partition, since you don't have a live cd.
Highlight the Ubuntu entry in the grub menu(if you're getting one), press "e" to edit, then change root from something like (hd0,1) to (hd0,2) and you'd probably also need to change the root in the kernel line accordingly...root=/dev/hda2 or root=/dev/hda3, etc...then press "b" to boot.  These changes are all temporary, but you might hit the right combination.

Creating ext3 filestystems can be problematic for Linux, using PartitionMagic.  The gparted live cd is much better for that:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

