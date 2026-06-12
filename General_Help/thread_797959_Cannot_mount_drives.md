---
title: "Cannot mount drives"
date: 2008-05-17
forum: General Help
---

### Post by dluu13 on 2008-05-17
Hi, I have Xubuntu 8.04 on this system, dual booted with Windows XP SP2.

I can't mount my drives for some reason.  Not only that, but I can't even see them.  They are all connected and they all show up when I'm in Windows.  I make sure that they're all properly dismounted before I boot into Linux, but it still doesn't work.  They're all in NTFS and I have NTFS support installed on this machine.  If there's anything missing please tell me because I'm very tired right now.

---

### Post by HalPomeranz on 2008-05-17
What output do you get when you run "sudo fdisk -l"?  That should show you the attached drives and the partitions on them...

---

### Post by dluu13 on 2008-05-18
> Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa238a238

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307        7476    49560525    5  Extended
/dev/sda5            1307        2612    10490413+  83  Linux
/dev/sda6            2613        2676      514048+  82  Linux swap / Solaris
/dev/sda7            2677        7476    38555968+   7  HPFS/NTFS

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb022b022

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2        7476    60042937+   5  Extended
/dev/sdb5               2        7476    60042906    7  HPFS/NTFS
That's the output.  I can see that linux is indeed recognizing the drives, but I do not know how to access them.

---

### Post by HalPomeranz on 2008-05-18
You can manually mount the NTFS partition on your second drive with a command like:

```
sudo mount -t ntfs /dev/sdb5 /media/windows
```

If you want the drive to be mounted automatically when the system boots, you would add a line to your /etc/fstab file like:

```
/dev/sdb5  /media/windows  ntfs    defaults,umask=007,gid=46 0       1
```

What's interesting is that my Gutsy install created the fstab entries for the Windows partitions on my system automatically.  I'm not certain why your install didn't update your fstab with the entries for the extra disks/partitions.

---

### Post by dluu13 on 2008-05-18
I got it fixed, just that now, I have to create folders as shortcuts to the mountpoint whereas usually, there is just the drive on the desktop.  It's just a minor annoyance that I can live with, but do you know about how to make it so that the actual drive shows up on the desktop.  

Thanks:D

---

### Post by HalPomeranz on 2008-05-18
> **dluu13 said:**
> I have to create folders as shortcuts to the mountpoint whereas usually, there is just the drive on the desktop.  It's just a minor annoyance that I can live with, but do you know about how to make it so that the actual drive shows up on the desktop.

I don't know the answer to that one.  Even on my machine, my Windows partition doesn't show up as a drive on my desktop.  The only drives I see as icons on my desktop are the ones that get auto-mounted by things like hald-- i.e. USB drives and CD/DVD-ROMs.  But I haven't tried to figure out the exact mechanism that causes these drive icons to show up in the GUI.

---

### Post by iahim on 2008-05-29
Just install NTFS Configuration Tool from the repository ... and use it :).

---

