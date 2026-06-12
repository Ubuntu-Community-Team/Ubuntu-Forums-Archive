---
title: "Installing grub on sdb1"
date: 2007-02-09
forum: General Help
---

### Post by MeathooK427 on 2007-02-09
I'm trying to install GRUB to the MBR so that I can boot my Ubuntu install, and I'm having the hardest time doing it. Here's my fdisk code: 

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12749   102406311    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7686    61737763+  83  Linux
/dev/sdb2            7687        9472    14346045    b  W95 FAT32
/dev/sdb3            9473        9729     2064352+  82  Linux swap / Solaris

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14945   120045681    7  HPFS/NTFS

```

I'm trying to install it with the following command in the terminal on the live cd:

```

sudo grub
root (hd0,0) **However, I've tried changing "hd to sdb, sd, hd2, etc."**
setup hd0

```

I know my problem lies in the "root (hd0,0)" line, just don't know what to change it to.

Also, on boot I get an error whenever it tries to load my ubuntu install, it's an Error 15.

Any help would be appreciated, thanks.

---

### Post by kebes on 2007-02-09
Linux is on "sdb1" which means: "SATA hard drive (sd), second hard drive (b), first partition (1)."

In grub nomenclature, this becomes "hd1,0", which means: "hard drive (hd), second hard drive (1), first partition (0)."

It's confusing because grub start counting at zero. So I believe the only change you need to make is your root line should be:

root (hd1,0)


Then do your "setup hd0" and it should be good (typically you install GRUB to the master boot record of the 1st hardrive, hd0). This will boot Linux, anyways. You may need to edit the file "/boot/grub/menu.lst" and add your Windows partition so it will dual-boot.


Hope that helps.



Note: I see that you have two SATA drives and one IDE drive. I'm not sure what order they are counted in... it probably depends on your BIOS. (Maybe go into BIOS and see what order it reports them in?... or check during bootup how it lists them?)

It's possible that in the discussion above you need to go "root (hd2,0) setup hd1" or something like that. It's hard to tell...

---

### Post by MeathooK427 on 2007-02-09
I tried root (hd1,0) and it takes fine, but when I do setup hd0 it gives

```

Error 11: Unrecognized device string

```

and if I put it in brackets, it gives:

```

Error 17: Cannot mount selected partition

```

---

### Post by kebes on 2007-02-09
Is it just the brackets missing:
root (hd1,0)
setup (hd0)

See grub manual:
[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)
(goto section 3.2)

---

