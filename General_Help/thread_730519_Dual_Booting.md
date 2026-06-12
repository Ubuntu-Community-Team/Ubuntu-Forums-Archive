---
title: "Dual Booting"
date: 2008-03-21
forum: General Help
---

### Post by Rob916 on 2008-03-21
I've installed Ubuntu some time ago.  I have one 160GB drive (SATA) dedicated to Windows XP, I have a second 160GB drive (PATA) dedicated to Ubuntu 7.10.  The problem I am having is I cannot boot into Ubuntu unless I have the Ubuntu CD in the drive.  If I have the CD out and turn the computer on it will boot into Windows, no boot menu.  If I insert the Ubuntu CD it will boot the CD and present me with the installation menu, I can scroll down to "Boot from first disk" or something of that nature and THEN I have the GRUB menu and I can boot Ubuntu from the hard drive.  I have not been able to find a definitive answer to go with my configuration.  How would I fix this so I do not require the CD to boot?

---

### Post by teryowen on 2008-03-21
go into your ubuntu, and then do this in terminal:

copy and paste the output

```

sudo fdisk -l

```

this will give us a picture and the names of all you're drives.

After you give us this information we will instruct you on how to install grub properly.

---

### Post by Rob916 on 2008-03-21
Here's what is spit out:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb969f15d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19080   153260068+  83  Linux
/dev/hda2           19081       19457     3028252+   5  Extended
/dev/hda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84428518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

---

### Post by teryowen on 2008-03-21
ok do the following in terminal:

```

sudo grub
root (hd0,0)
setup (hd0)
quit

```

now also make sure that in you're BIOS that the priority for booting is set to the harddrive with ubuntu on it. This should work if it doesnt try replacing the (hd0,0) with (hd1,0) and the (hd0) with (hd1) but what i put above should work.

---

### Post by Rob916 on 2008-03-21
After reading your reply about changing the first boot device to the Ubuntu drive I tried that without doing anything to GRUB.  It worked!  The Ubuntu community is awesome.  Thank you for your help!

Robert

---

