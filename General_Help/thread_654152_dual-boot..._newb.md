---
title: "dual-boot... newb"
date: 2007-12-30
forum: General Help
---

### Post by hydramatic on 2007-12-30
I'm trying to get my machine to dual boot. From the topics I found on google it appeared I needed to modify the /boot/grub/menu.lst file.. I did that, here is what I added:

title Microsoft Windows
root (hd1,0)
savedefault
makeactive
chainloader +1

I'm pretty sure it's on hd1 but honestly I'm not 100% I only think that because ubuntu is set on hd0,0 (Windows is installed on another HDD). The only other drive I have besides those 2 is my external via 1394

Anyway, when I attempt to boot into my newly added Windows option, the computer seems to freeze at 'Starting up' screen. So I'm not to sure what to do now.

---

### Post by kyphi on 2007-12-30
You have not provided sufficient information.

What type of hard drives are installed, PATA or SATA - are they both the same type.

The first thing to do is to remove the changes you have made.

Next, in a terminal type ```
sudo fdisk -l
``` to get a listing of your drives.  Would you post the results in your reply.

---

### Post by bernied on 2007-12-30
If the Windows install really is on the second bios drive (hd1 to grub), then you need to use the map command in grub. This can be used to tell windows that it is running on the first drive, which is where it likes to be. Try adding the two map commands to your menu.lst file:
```
title windows
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```You can leave the savedefault and makeactive commands in if you like, but savedefault can cause trouble, and makeactive is not necessary in this case.

---

### Post by hydramatic on 2007-12-30
Kyphi

```

Disk /dev/hdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd1dbd1d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4787    38451546   83  Linux
/dev/hdc2            4788        4998     1694857+   5  Extended
/dev/hdc5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4c6f4c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0cb49b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

```

The first disk (41gb IDE) holds ubuntu, the 2nd disk (200gb SATA) has the windows installation

Bernied, thanks for your reply. In the mean time I will try what you have suggested and will let you know what happened!

---

### Post by bernied on 2007-12-30
That fdisk output looks like three disks. Are you sure you only have two? (Maybe one is a cd/dvd?)

Regardless of how many disks you have, your solution depends on how the grub bootloader perceives the disks. You can find out using the grub console and TAB-completion. [Herman](http://www.users.bigpond.net.au/hermanzone/p15.htm#cli) describes this better than me.

---

### Post by hydramatic on 2007-12-30
The 3rd disk is my external HDD.

Ok, now my message is NTLDR is missing. I'm going to try and create a boot cd-rom and attempt to boot windows

---

### Post by hydramatic on 2007-12-30
Ok well after I got into windows I found that the 3 crutial boot files were missing.. I haven't figured out why considering I had windows installed on that PC for a whole 24 hours. But now I can happily switch between OS

Thanks bernied!

---

### Post by bernied on 2007-12-31
Happy days! You are welcome.

---

