---
title: "Lost Windows partition! Help!"
date: 2008-04-24
forum: General Help
---

### Post by rwheelock83 on 2008-04-24
Hey guys, I just finished installing Ubuntu 64 bit 7.10 for the first time on a new partition. The first time I booted up, the original Windows partition (Vista) showed up on the Ubuntu desktop. I rebooted and tried to boot up Windows, but after about 2 seconds of the loading screen, it restarts. Now, the Windows partition doesn't appear on the desktop anymore. Any ideas?

Thanks!

---

### Post by kilroy423 on 2008-04-24
> I rebooted and tried to boot up Windows, but after about 2 seconds of the loading screen, it restarts.

Sounds like grub is pointing to the wrong place to Windows, or your Windows partition is corrupt.

```
sudo fdisk -l
```

Will list all your disks and partitions, from there you can mount your Windows partition.

```
mkdir windows
sudo mount /dev/DISK /yourfolderpath/windows
```

That should mount your Windows partition to wherever you want.  DISK is the location that fdisk reported your partition.

Kilroy

---

### Post by Cannaregio on 2008-04-24
Also have a look at your disk structure using gparted

```
sudo gparted
```

there you'll see exactly
1) where is/are your NTFS partition/s (and everything else on your disks)
2) what is/are its/their name/s
write these data down, you'll need it/them to correct your [COLOR="Blue"]boot/grub/menu.lst[/COLOR]

---

### Post by rwheelock83 on 2008-04-24
I was able to mount the partition, but any time I put in a path at the end of it, it says no such file or directory, so now I can get to it through /media/sda2. (You'll have to forgive me, I'm very new, as in a couple hours new, to the Linux file system, command line system, etc...)

When I run sudo gparted, it says command not found... Is this some kind of add on or utility that I need to download?

Thanks

---

### Post by rwheelock83 on 2008-04-24
Here is the fdisk information:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x209b4b29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       15997   126953125    7  HPFS/NTFS
/dev/sda3           15998       19457    27792450    5  Extended
/dev/sda5           15998       19279    26362633+  83  Linux
/dev/sda6           19280       19457     1429753+  82  Linux swap / Solaris

```

And the relevant part of the menu.lst file:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

I'm sure sda2 is the correct partition, but one of those others is probably a recovery/backup partition from the factory. Is it possible that it's trying to boot from that partition instead?

---

### Post by rwheelock83 on 2008-04-24
Sorry to keep adding on, but after rebooting to Windows (trying to, rather), and selecting repair installation, it will look for installations of Windows, and find none. It asks for the location of a HDD driver, and when I browse for it, it shows all partitions of the drive. The "Toshiba Recovery" partition and the linux partition will both show how much free space they have, but the original windows partition does not. When I check properties, it says 0 bytes free of 0 bytes.

After booting back up to Ubuntu, the partition is back on the desktop, and I can access all the files that should be there and see 37GB free.

---

### Post by rwheelock83 on 2008-04-24
to the top...

---

### Post by retrow on 2008-04-24
> **rwheelock83 said:**
> When I run sudo gparted, it says command not found... Is this some kind of add on or utility that I need to download?Thanks
Yes, gparted is a partition editor program under Ubuntu. You can get it by running

```
sudo apt-get install gparted
```

But be very careful what you do. Just look up the necessary disk information through gparted, but don't try modifying the partitions unless you know exactly what you are doing.

---

### Post by rwheelock83 on 2008-04-24
Ok... gparted (thanks, retrow) shows partition /dev/sda2 is ntfs, mountpoint /media/sda2, 88.20 GiB used,32.87 GiB free, and is flagged "boot". Anything there look out of the ordinary, or other information I need to get?

Thanks guys

---

### Post by retrow on 2008-04-24
When Grub loads and you scroll down to boot with Vista, what error do you get? From the partition table it seems like everything is in order.

Once my sister's machine had a similar error, and I had to change the listing in menu.lst to (hd0,2) instead of the default (hd0,1) for Windows. If there's more than one hard drive, it could also be (hd1,1).

---

### Post by rwheelock83 on 2008-04-25
Tried it, got:

Error 12: Invalid device requested

---

### Post by rwheelock83 on 2008-04-25
to the top...

---

### Post by rwheelock83 on 2008-04-25
Any ideas?

---

