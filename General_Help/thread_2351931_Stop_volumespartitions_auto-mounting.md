---
title: "Stop volumes/partitions auto-mounting"
date: 2017-02-07
forum: General Help
---

### Post by tharmund on 2017-02-07
New to Linux. I use Lubuntu, my windows partitions mount everytime I  use the Linux OS, is there any way to keep them from auto-mounting?
  and how can I mount a partition when I want to?
  Assume that my Fat32 partition is  /dev/sda5

---

### Post by Bucky Ball on 2017-02-07
Please open a terminal, open this file:

```
nano /etc/fstab
```

... and post it here between code tags, please (see the link in my signature for how). (If you have Gedit then replace 'nano' in the last command with 'gedit' and it should open in Gedit.) 

Then run this command:

```
sudo blkid
```

Assuming is a waste of time and will lead to confusion and mistakes. Make sure your FAT partition is sda5 on the output of that last command and confirm. Post the output of that command here, please, between code tags again.

---

### Post by tharmund on 2017-02-08
Once again, it is a FAT32 partition with data, I dont want it to be auto-mounted, but mounted at anytime I want to.

```
/dev/sda5: UUID="B9C1-DD76" TYPE="vfat" PARTUUID="0aa163f7-06"
```

---

### Post by SeijiSensei on 2017-02-08
Comment out the corresponding entry in /etc/hosts by putting a hash mark ("#") at the beginning of the line.

If you want to mount the device on-the-fly use
```
sudo mount /dev/sda5 /path/to/mount/point
```
where /path/to/mount/point points to an empty directory where the filesystem will be mounted.  Linux will usually recognize FAT32 filesystems automatically.

---

### Post by ajgreeny on 2017-02-08
As it is fat32 it will appear in the Places in your file manager and simply clicking that will mount it and should be read/write.

All /etc/fstab does is mount it automatically at boot, which you say you don't want.
Did you edit fstab already by adding the line to mount it at boot, as that would not happen without some action from you?

---

### Post by tharmund on 2017-02-08
When  I open the fstab file, I only see two entries, the Linux OS partition and the swap partition,   and yet the FAT32 partition auto-mounts, that I only need to open File Manager and the  partition will be already mounted.        What I want is the FAT32 partition not to be auto-mounted and only mounted on the fly when request it with a command.

When I use the sudo blkid command, the Linux OS partition and swap partition appear and the FAT32 partition...

---

### Post by tharmund on 2017-02-08
```
sudo mount /dev/sda5 /path/to/mount/point
```

If I successfully figure out how to stop partitions from auto-mounting,   your command AS YOUR WROTE IT, will mount my partition on the fly?

---

### Post by SeijiSensei on 2017-02-08
Well, as I said, you need to specify "/path/to/mount/point" like "/media/mydisk" or something like that.  You'll need to create an empty directory first:
```
sudo mkdir /media/mydisk
```

You might also need to specify broader or narrower permissions than the default.  If you want to make the filesystem available only to you, add
```
sudo chown yourusername:yourusername /media/mydisk
sudo chmod 700 /media/mydisk

```
Then run the "mount" command I gave before.  These commands make the mount point owned by you, and only you can write to it.

---

### Post by ajgreeny on 2017-02-09
> **SeijiSensei said:**
> Well, as I said, you need to specify "/path/to/mount/point" like "/media/mydisk" or something like that.  You'll need to create an empty directory first:
```
sudo mkdir /media/mydisk
```

You might also need to specify broader or narrower permissions than the default.  If you want to make the filesystem available only to you, add
```
sudo chown yourusername:yourusername /media/mydisk
sudo chmod 700 /media/mydisk

```
Then run the "mount" command I gave before.  These commands make the mount point owned by you, and only you can write to it.
Do those two last chown and chmod commands work on a mountpoint of a fat32 partition; I thought not.

---

### Post by SeijiSensei on 2017-02-09
Just because FAT32 doesn't support permissions doesn't mean that the OS ignores them.  From the point of view of Linux, what's attached to the mount point is largely irrelevant.

---

