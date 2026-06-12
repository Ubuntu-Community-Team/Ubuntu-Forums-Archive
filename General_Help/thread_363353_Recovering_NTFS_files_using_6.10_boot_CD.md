---
title: "Recovering NTFS files using 6.10 boot CD?"
date: 2007-02-16
forum: General Help
---

### Post by hamdodger on 2007-02-16
Is there a way to us the Ubuntu 6.10 CD to boot a system that has corrupt Windows XP installation (NTFS formatted), and then mounting the NTFS partition and potentially a FAT32 formatted USB drive, to be able to pull off non corrupted data (i.e. Word, Excel files) and transfer it to the FAT32 drive so that I can at least recover the raw data?  

I'm fine with having to redo the entire system after recovery, but I'd like to be able to at least try to salvage the data files from the system before doing that and using the Ubuntu bootable ISO seems like a perfect solution for doing so.

Thanks in advance!

---

### Post by taurus on 2007-02-16
You need to mount your harddrive where ntfs is from the LiveCD.  However, the USB harddrive should be automounted when you plug it in.  Boot from the LiveCD and post the output of this command so I know where is your harddrive.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by hamdodger on 2007-02-16
The NTFS volume is /dev/hda1.

---

### Post by taurus on 2007-02-17
Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
df -h
```

---

### Post by hamdodger on 2007-02-19
My mistake.  The hard drive device is at /dev/sda1 and when I attempt to mount it using the previous command that you outlined, I get a mount error stating:

wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or other error

However I know that this drive didn't have any actual hardware or filesystem failure.   It was all about a user loading an incorrect serial ATA driver under XP, so the drive won't boot into Windows anymore, hence why I need to pull data off it using an Ubuntu boot CD.

Is it just because the mount parameters change if the drive is a SATA device, versus an ATA or SCSI device?

---

### Post by taurus on 2007-02-19
What's the output of this command from a terminal then?

```
sudo fdisk -l
```

---

### Post by hamdodger on 2007-02-19
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

---

### Post by taurus on 2007-02-19
What happens if you just run

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows
```

---

### Post by hamdodger on 2007-02-19
OK I've been able to successfully mount the volume, but what can I do to be able to access the /media/windows volume from the default user (ubuntu) desktop GUI?  Currently the  volume is owned by root so I don't have permissions to access it via the Gnome desktop as user 'ubuntu'.

---

### Post by taurus on 2007-02-19
From a terminal, run

```
gksudo nautilus
```
and browse to /media/windows.  You are now running nautilus file manager as root.

---

### Post by hamdodger on 2007-02-19
Worked like a charm.

Much thanks! :)

---

### Post by skrishnan on 2007-02-19
I am in a similar situation trying to recover one of the NTFS (W2K) partition using a live CD. I was able to mount the partition, and I have permission to read. However, when I try to copy a large (>200 MB) file onto a USB device (1 GB), it copies only 4 MB and stops. I tried various commands including cp, gzip, tar but no luck.

---

