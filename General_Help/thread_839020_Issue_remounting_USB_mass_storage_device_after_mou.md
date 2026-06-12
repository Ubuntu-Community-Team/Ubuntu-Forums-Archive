---
title: "Issue remounting USB mass storage device after mount point change"
date: 2008-06-24
forum: General Help
---

### Post by Lyk4n on 2008-06-24
Well I guess I've messed it up again guys. I was (stupidly) trying to change the mount point on my 160 GB usb drive.

It was originally "/media/WD Passport" I didn't like the name of the drive so I changed the mount point to "media/Backup Disk"

Then I proceeded to unmount the drive and plug it back in. I immediately get this error message:

Unable to mount the volume 'WD Passport'.
Details:
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I'm completely lost on fixing it, can anyone help me out?

---

### Post by p_quarles on 2008-06-24
What did you do to change the mount point? 

Beyond that, can you post the results of this?
```
sudo /sbin/fdisk -l
```
(with the drive plugged in, of course)

---

### Post by Lyk4n on 2008-06-24
I right clicked on the icon that was on my desktop for the drive and went to properties and then volume and clicked the down arrow for settings and typed in the new mount point I wanted for the drive. I should have read up a little more before doing something dumb like this..

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b094

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8393    67416741   83  Linux
/dev/sda2   *        8394       14767    51199155    7  HPFS/NTFS
/dev/sda3           14768       29793   120696345   83  Linux
/dev/sda4           29794       30401     4883760   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)


The /dev/sdb1 is the drive I'm talking about.. I can still see it, it just won't let me mount it so I can't access it.. Thanks for the help!

---

### Post by p_quarles on 2008-06-24
Hmm. Well, I don't know enough about how Gnome handles disk labels to answer the question, but I can offer an easy workaround until someone else offers a fix:
```
pmount /dev/sdb1
```
That will mount the drive under /media/sdb1, and will do this as the current user (so the permissions will not get in the way).

---

### Post by iaculallad on 2008-06-24
Try to unmount the drive first:

```
sudo umount /dev/sdb1
```

Create a new mountpoint for your /dev/sdb1 drive:

```
sudo mkdir /mnt/USBDrive
```

Mount your FAT32 drive to /mnt/USBDrive

```
sudo mount -t vfat /dev/sdb1 /mnt/USBDrive
```

---

### Post by Lyk4n on 2008-06-24
I just did what iaculallad said to do. I can now access the drive like a folder. Very big thanks for that! Is there no way to actually fix what I did?

---

