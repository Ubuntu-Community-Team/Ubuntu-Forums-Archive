---
title: "Grub"
date: 2008-04-08
forum: General Help
---

### Post by Gauvenator on 2008-04-08
This is not related to Ubuntu, but is to its boot loader Grub.

I recently installed another distribution of linux on a different hardrive while my Windows hdd was unplugged.  Both OS'es still work, but I have to choose which one to boot from in the BIOS.

How can I configure grub to boot Windows also?

---

### Post by bodhi.zazen on 2008-04-08
Just add a stanza for your windows partition to /boot/grub/menu.lst

> title Windows
root (hdx,y)
makeactive
chainloader +1

You just need to know the grub designation for your windows partition. It is likely either 

(hd0,0) or (hd1,0)

See this link : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by Gauvenator on 2008-04-08
> **bodhi.zazen said:**
> Just add a stanza for your windows partition to /boot/grub/menu.lst



You just need to know the grub designation for your windows partition. It is likely either 

(hd0,0) or (hd1,0)

See this link : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Ah I believe it would be hd1,0 as that it is the second hardrive in the system.

Now since window's bootloader is still there, will grub still be able to boot it?

---

### Post by bodhi.zazen on 2008-04-08
Yes, that is what "chainloader" does, passes the boot process to the windows partition.

---

### Post by Gauvenator on 2008-04-08
Awesome thanks!  I'll try it out in a minute...

---

### Post by Gauvenator on 2008-04-08
I tried :

title Windows XP Professional x64
rootnoverify (hd1,0)
makeactive
chainloader +1

title Windows XP Professional x64
root (hd1,0)
makeactive
chainloader +1

title Windows XP Professional x64
rootnoverify (hd1,0)
chainloader +1

and none worked.

I'm suspecting now my hardrive selection is incorrect, as each time it displays the entry and the cursor just blinks.

What command can I use to determine the locations of all disks in the system?  I don't have gparted.

---

### Post by Gauvenator on 2008-04-08
I ran fdisk -l and got this:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d5b49ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        6079    29294527+  83  Linux
/dev/sda3            6080        6565     3903795   82  Linux swap / Solaris

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aea20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20022   160826683+   7  HPFS/NTFS
```

What should I use as Windows's hardrive in Grub?

---

### Post by bodhi.zazen on 2008-04-08
Looks like you need to "map" your windows install.

> title Windows
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

---

### Post by matey3 on 2008-04-08
the nice thing about the grub is that you can hit e and edit the lines then b to boot from them so it seems like you should try sd1,0 instead of hd1,0. (i think sd is for scsi drives)

also try different numbers like sd2,1 sd1,1 or whatever...it wont hurt. just remember the one that works for you so you can edit your menu.lst and save it so u wont have to do the manual startup every time. (I had to figure  this out on my own and at my new job) eek. it was scarey lol..

but thanks to all who replied. I learned a new thing too...

good luck.

---

### Post by bodhi.zazen on 2008-04-08
> **matey3 said:**
> the nice thing about the grub is that you can hit e and edit the lines then b to boot from them so it seems like you should try sd1,0 instead of hd1,0. (i think sd is for scsi drives)

also try different numbers like sd2,1 sd1,1 or whatever...it wont hurt. just remember the one that works for you so you can edit your menu.lst and save it so u wont have to do the manual startup every time. (I had to figure  this out on my own and at my new job) eek. it was scarey lol..

but thanks to all who replied. I learned a new thing too...

good luck.

grub does not refer to hard drives the same way as linux (fstab or fdisk), so "sdx,y" will not work with grub.

See this link or grub documentation.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Gauvenator on 2008-04-08
Thanks so much!  The mapping options worked perfectly.

---

