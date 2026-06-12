---
title: "Can't find hard drives"
date: 2007-02-08
forum: General Help
---

### Post by MadMac on 2007-02-08
Howdy!

Bit of a newbie here, but not too bad - I was a "DOS weinie" in another life, so the command line doesn't scare me too badly.   ;)

Anyway, my problem is that I cannot get Ubuntu 6.10 to show me the other two hard drives and will only show one of the two DVD-Rs I have in the computer.

I did the "$sudo fdisk -l" and here is the result:

===============

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4678    37576003+  83  Linux
/dev/hdb2            4679        4865     1502077+   5  Extended
/dev/hdb5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1        9729    78148161    7  HPFS/NTFS

==============

When I go into the file manager, I can find the folders of /dev /hda, hda1, hdb, hdb1, hdb2, hdb5, hdf, hdf1.  However, each one of those hd files has a red X on the corner and when I try to open them (click on it) I get what seems to be a generic error code that ends with "No application is known for this kind of file.”

I am dual booting with XP Home and Grub seems to be working fine.  I can boot into which ever one I want to, IOW.

Oh, one of the hard drives is on a PCI hard drive controller card, but is not set up for RAID, it is just a file storage drive, no OS.

Any ideas?

Thanks!

Michael

---

### Post by cleentrax on 2007-02-08
are the drives showing up in /media?

---

### Post by MadMac on 2007-02-08
Cleentrax,

What is showing up in /media is:  CDROM, CDROM0, CDROM1, FLOPPY and FLOPPY0.

When I click on them it just goes to an empty directory.

Hope that helps!

Thanks!

---

### Post by taurus on 2007-02-08
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdf1   /media/hdf1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create the two new mount points and mount them

```
sudo mkdir /media/hda1 /media/hdf1
sudo mount -a
df -h
```

---

### Post by MadMac on 2007-02-08
Taurus,

That seemed to do it.  However, I still have two floppy drives with one that will not mount.  Can I delete that one?  (Error is: "mount: /dev/ is not a block device")

Also, the two hard drives came up as hda1 and hdf1, is that okay?

Oh, and both hard drives now have icons on the desktop - can they be moved/deleted/whatever?  No biggie on  that, just wondering. 

Lastly, it only shows one of the DVD drives.  It's the master drive, it's not finding the slave.

All in all, though, great advice and assistance!  I thank you!  :KS   \\:D/ 

Michael

---

### Post by taurus on 2007-02-08
> **MadMac said:**
> Taurus,

That seemed to do it.  However, I still have two floppy drives with one that will not mount.  Can I delete that one?  (Error is: "mount: /dev/ is not a block device")

Instead of deleting it, put a # in front of it to comment out.

> Also, the two hard drives came up as hda1 and hdf1, is that okay?

Now, you know which drive is which.

> Oh, and both hard drives now have icons on the desktop - can they be moved/deleted/whatever?  No biggie on  that, just wondering. 

You don't want the icons on your desktop!  You can mount them somewhere else like 

/mnt/hda1
/mnt/hdf1

and they will not appear on your desktop.  However, you can still access them either from a terminal or with nautilus.  And if you decide to replace /media/hda1 with /mnt/hda1 (and /media/hdf1 with /mnt/hdf1), don't forget to create those two new mount points, /mnt/hda1 & /mnt/hdf1, or /etc/fstab won't be able to mount them.

> Lastly, it only shows one of the DVD drives.  It's the master drive, it's not finding the slave.

All in all, though, great advice and assistance!  I thank you!  :KS   \\:D/ 

Michael

Can you post your /etc/fstab?

```
cat /etc/fstab
```

---

### Post by MadMac on 2007-02-08
[QUOTE=taurus;2126690]Instead of deleting it, put a # in front of it to comment out.

Not sure on how to do this.  Can you explain, please?


Now, you know which drive is which.

Yup.  It helps, that's for sure!


You don't want the icons on your desktop!  You can mount them somewhere else like 

/mnt/hda1
/mnt/hdf1

and they will not appear on your desktop.  However, you can still access them either from a terminal or with nautilus.  And if you decide to replace /media/hda1 with /mnt/hda1 (and /media/hdf1 with /mnt/hdf1), don't forget to create those two new mount points, /mnt/hda1 & /mnt/hdf1, or /etc/fstab won't be able to mount them.

Okay, I am a bit lost here.  Again, I am not that spiffy on doing mounts and unmounts.  I can believe that I don't need them on the desktop.  They show up in both my computer and places menu, as well.


Can you post your /etc/fstab?

Here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=524f049a-2124-4d91-8924-19866f94205e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=604b621c-3a17-4cb0-bd40-2311a5a1c701 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/hda1     ntfs   nls=utf8,umask=0222   0   0
/dev/hdf1       /media/hdf1     ntfs   nls=utf8,umask=0222   0   0


Oh.  I'm not too sure, but I have a sneaking suspicion that I may not have nautilus installed - I can't find anything with that name, not even in the Add/Remove menu.  I have been using Home Folder from the Places menu to get where I need to go.

Thanks again!!

---

### Post by taurus on 2007-02-08
```
gksudo gedit /etc/fstab
```
And make it look like this.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=524f049a-2124-4d91-8924-19866f94205e / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5
UUID=604b621c-3a17-4cb0-bd40-2311a5a1c701 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
#/dev/ /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /mnt/hda1 ntfs nls=utf8,umask=0222 0 0
/dev/hdf1 /mnt/hdf1 ntfs nls=utf8,umask=0222 0 0

```
Save it.  Now, create those two new mount points.

```
sudo mkdir /mnt/hda1 /mnt/hdf1
```
Reboot and your ntfs drives are now mount to /mnt/hda1 & /mnt/hdf1.

And for the slave DVD drive, there is nothing when you insert a DVD into the drive, /dev/hdd?

---

### Post by MadMac on 2007-02-09
> **taurus said:**
> ```
gksudo gedit /etc/fstab
```
And make it look like this.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=524f049a-2124-4d91-8924-19866f94205e / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5
UUID=604b621c-3a17-4cb0-bd40-2311a5a1c701 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
#/dev/ /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /mnt/hda1 ntfs nls=utf8,umask=0222 0 0
/dev/hdf1 /mnt/hdf1 ntfs nls=utf8,umask=0222 0 0

```
Save it. 

Okay, this worked.

 Now, create those two new mount points.

```
sudo mkdir /mnt/hda1 /mnt/hdf1
```
Reboot and your ntfs drives are now mount to /mnt/hda1 & /mnt/hdf1.

They are still showing on the desktop.  And are still able to be accessed.

And for the slave DVD drive, there is nothing when you insert a DVD into the drive, /dev/hdd?

It works, but kind of funky.  It is using the one icon for both DVD drives.  If I put a CD in each drive, the icon shows the one that was "recognized" (i.e. loaded) first.  No way to see both DVD drives at once.

Thanks!

---

### Post by taurus on 2007-02-09
What's the output of this command from a terminal?

```
ls -la /media
```

---

### Post by MadMac on 2007-02-09
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la /media
```

Here it is:

~$ ls -la /media
total 36
drwxr-xr-x  7 root root 4096 2007-02-08 18:54 .
drwxr-xr-x 21 root root 4096 2007-02-07 15:26 ..
lrwxrwxrwx  1 root root    6 2007-02-07 15:11 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-02-07 15:11 cdrom0
drwxr-xr-x  2 root root 4096 2007-02-07 15:11 cdrom1
lrwxrwxrwx  1 root root    7 2007-02-07 15:11 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-02-07 15:11 floppy0
dr-xr-xr-x  1 root root 8192 2007-02-06 21:26 hda1
dr-xr-xr-x  1 root root 8192 2007-01-30 19:06 hdf1

The line with "cdrom -> cdrom0" is highlighted differently.  Same as with the "floppy -> floppy0".  The ones to the left of the "->" are highlighted a different color.


Thanks!

---

### Post by taurus on 2007-02-09
It's called a link.  What if you remove /media/cdrom.  

```
sudo rmdir /media/cdrom
```
Reboot and see if you see two icons when you insert two DVDs into both drives?

---

### Post by MadMac on 2007-02-09
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la /media
```

Here it is again. (I think the first post was eaten by the bit-gods.)

desktop:~$ ls -la /media
total 36
drwxr-xr-x  7 root root 4096 2007-02-08 18:54 .
drwxr-xr-x 21 root root 4096 2007-02-07 15:26 ..
lrwxrwxrwx  1 root root    6 2007-02-07 15:11 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-02-07 15:11 cdrom0
drwxr-xr-x  2 root root 4096 2007-02-07 15:11 cdrom1
lrwxrwxrwx  1 root root    7 2007-02-07 15:11 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-02-07 15:11 floppy0
dr-xr-xr-x  1 root root 8192 2007-02-06 21:26 hda1
dr-xr-xr-x  1 root root 8192 2007-01-30 19:06 hdf1

The two items to the left of the "->" are both highlighted a different color from the others, if that makes any difference.

Thanks!

---

### Post by MadMac on 2007-02-09
> **taurus said:**
> It's called a link.  What if you remove /media/cdrom.  

```
sudo rmdir /media/cdrom
```
Reboot and see if you see two icons when you insert two DVDs into both drives?

Here is what I get:

desktop:~$ sudo rmdir /media/cdrom
rmdir: /media/cdrom: Not a directory

Weird, because I do have a media folder in nautilus
(Yeah, I know where that is, now.  Thanks for not laughing at me.)

Okay, I did a check while writing this and now I have both drives showing up in "Places" and in the file manager under "computer".  I dunno.  :-# 

Now, if I can get your help to remove the two hard drive icons from the desktop, that would be grand!  [-o<

Thanks!

---

### Post by taurus on 2007-02-09
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace these two lines

```

/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdf1   /media/hdf1   ntfs   nls=utf8,umask=0222   0   0

```
with these two new lines

```

/dev/hda1   /mnt/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdf1   /mnt/hdf1   ntfs   nls=utf8,umask=0222   0   0

```
Then, create two new mount points

```
sudo mkdir /mnt/hda1 /mnt/hdf1
```
and reboot.

---

### Post by MadMac on 2007-02-09
> **taurus said:**
> Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace these two lines

```

/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdf1   /media/hdf1   ntfs   nls=utf8,umask=0222   0   0

```
with these two new lines

```

/dev/hda1   /mnt/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdf1   /mnt/hdf1   ntfs   nls=utf8,umask=0222   0   0

```
Then, create two new mount points

```
sudo mkdir /mnt/hda1 /mnt/hdf1
```
and reboot.

Alrighty then.  It took both of them off the desktop.  The problem is that Nautilus now is not showing them (Places then Computer).  I know what they are so would it be a big problem if I just left them on the desktop?

Thanks!

---

### Post by taurus on 2007-02-09
Doesn't really matter where you mount them, /media or /mnt, as long as you know where they are.

---

### Post by MadMac on 2007-02-09
> **taurus said:**
> Doesn't really matter where you mount them, /media or /mnt, as long as you know where they are.

Okay.

Thanks again for all your assistance and advice!  =D> 

Michael

---

