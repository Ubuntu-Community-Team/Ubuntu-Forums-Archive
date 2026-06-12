---
title: "Really Confused"
date: 2007-11-12
forum: General Help
---

### Post by Grindordie on 2007-11-12
Hello there, 
I've been using Ubuntu for about 2 months and I am very pleased.


The Primary Master is my Ubuntu drive, the Primary Slave is my storage drive and I've attached my Windows XP drive (40gb) to the Secondary Slave slot. (The Secondary Master is my CD drive).

I added the following line to my /boot/grub/menu.lst 
```

title		Microsoft Windows XP Home HD3
root		(hd3,0)
savedefault
makeactive
chainloader	+1

```

But when I choose the Windows option to boot Window it tells me there isnt a drive...
so I tried
changing 
root		(hd3,0)
to 
root		(hd2,0)
and
root		(hd1,0)

and when I run it at hd2 or hd1, it just stalls at "Please wait..." or something like it.

My current setup is as follows:
200gb for Ubuntu (hda)
200gb for Storage (hdb)
40gb for Windows (hdd)

Here is my fdisk -l output
```

root@grind-desktop:/home/grind# fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf792595

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24415   196113456   83  Linux
/dev/hda2           24416       24792     3028252+   5  Extended
/dev/hda5           24416       24792     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0582bb37

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/hdd: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4997    40138371    7  HPFS/NTFS


```

How can I make it boot?

Thank you,
Grind

---

### Post by rsambuca on 2007-11-12
Windows really doesn't like to live anywhere except the primary partition of the first drive.  You will probably have to use the map command to 'trick' XP into thinking it is where it likes...

Try something along these lines:
```

title   Windows XP
rootnoverify  (hd3,0)
makeactive
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1
```

EDIT:  You might also want to double check your jumpers on the drives.

---

### Post by Grindordie on 2007-11-12
Thank you it worked, the only thing I changed was hd3 to hd2, somehow hd3 isn't the slot... Its weird, but it works.

So this worked:
```
title   Windows XP
rootnoverify  (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

Thank you :)

---

### Post by Grindordie on 2007-11-12
It worked fine until I restarted the computer...
Now I get "NTLDR is missing..." and it doesn't load.

Not even 1 minute into Windows and already giving me problems.

I'll look into the error.

---

