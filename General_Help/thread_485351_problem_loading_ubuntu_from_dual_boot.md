---
title: "problem loading ubuntu from dual boot"
date: 2007-06-26
forum: General Help
---

### Post by christophdanger on 2007-06-26
ok, so i had a dual boot system running for awhile xp/fiesty.  i reinstalled windows to the correct partition and grub didn't load, i just booted straight into windows.  i reinstalled grub, it recognizes everything that it did before, but when i select ubuntu it gives me an error 17.

i checked some other documentation and it said that error 17 means the operating system is there but the file format cannot be read by grub?  doesn't make any sense to me, i didn't change anything on my ubuntu side of hd.   i checked fdisk.

[I]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15659   125780886    7  HPFS/NTFS
/dev/sda2           15660       15908     2000092+  82  Linux swap / Solaris
/dev/sda3           15909       30401   116415022+  83  Linux
[/I]

i'm pretty much a newb when it comes to linux but i can get around with help.

any ideas?

---

### Post by merlinus on 2007-06-26
Check entries in /boot/grub/menu.lst to make sure everything is pointing to the correct partitions.

SuperGrub may be useful:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by christophdanger on 2007-06-26
i don't know how i could access that directory, i'm on a live cd... well now in windows, but about to be back on the live cd...lol

---

### Post by merlinus on 2007-06-26
SuperGrub may be easiest....

-merlin

---

### Post by confused57 on 2007-06-26
> **christophdanger said:**
> i don't know how i could access that directory, i'm on a live cd... well now in windows, but about to be back on the live cd...lol

You can mount your root partition with the live cd, then access your /boot/grub/menu.lst:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by christophdanger on 2007-06-26
ok i did all that and i can see my menu.lst file.

hmmm 

it says the root for all ubuntu stuff is (hd0,1)

and window is (hd0,0)

now i don't know if that's right or not?

here's my partition table.

wait, it's the same as before.

---

### Post by confused57 on 2007-06-26
> **christophdanger said:**
> ok i did all that and i can see my menu.lst file.

hmmm 

it says the root for all ubuntu stuff is (hd0,1)

and window is (hd0,0)

now i don't know if that's right or not?

here's my partition table.

wait, it's the same as before.
Looks like your root partition is (hd0,2), your menu.lst is showing (hd0,1)...what you can do is boot your computer, highlight your Ubuntu entry in the grub boot menu, press "e", then change root to (hd0,2), then press "b" to boot...(you will need to press "e" again to edit the root entry),  this change is temporary, but you can make it permanent if it works.

---

### Post by christophdanger on 2007-06-26
yep that's exactly what it was...

ahhh it feels good to be sitting in my old install and not the live cd....

ahhhh....


thanks confused57 and merlinus.  it really helped me out and i appreciate it.;)

---

