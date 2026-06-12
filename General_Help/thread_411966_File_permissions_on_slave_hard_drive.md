---
title: "File permissions on slave hard drive"
date: 2007-04-17
forum: General Help
---

### Post by Dave54 on 2007-04-17
With Feisty Fawn coming out soon, I'm backing up all my files to a slave hard drive I installed. I used gparted to format it as 1 partition in ext3.

So, when I boot up with the hard drive installed, it automatically mounts and I get an icon on my desktop. I can view it, but it doesn't let me add/move files. "You do not have the permissions required" or something like that.

So I unmount it and run
```
sudo fdisk -l
```
which outputs:
```
dave@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30119   241930836   83  Linux
/dev/hda2           30120       30401     2265165    5  Extended
/dev/hda5           30120       30401     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7299    58629186   83  Linux
```
Obviously, I want "hdb1". Now I run
```
sudo mkdir /media/slavedrive
```
to make the mount point I want to use. I now run
```
sudo gedit /etc/fstab
```
and find that /dev/hdb1 is already there. I delete that line and add
```
/dev/hdb1 /media/slavedrive ext3 rw,user 0 2
```
so my fstab now looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/hda1
UUID=892e6823-debf-4d05-9de7-de98068714fe  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/hda5
UUID=495617f0-1283-4fce-90c4-1af068c57ee1  none            swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto              0  0  
/dev/hdb1                            /media/slavedrive     ext3         rw,user                    0  2  
```
I save the file and run
```
sudo mount -a
```
to mount it. I get the icon on my desktop called "slavedrive". If I try to move a file into it, it says:
> You do not have permissions to write to this folder.
What did I do wrong?:confused:

---

### Post by taurus on 2007-04-17
Change the entry for /dev/hdb1 back to

```
/dev/hdb1   /media/slavedrive   ext3   defaults   0   2
```
Then, change the ownership of /media/slavedrive from root to whatever your login name is, assuming it's **dave**.

```
sudo chown -R **dave**:**dave** /media/slavedrive
sudo chmod -R 755 /media/slavedrive
ls -la /media
```

---

### Post by Dave54 on 2007-04-17
Thanks, but I have a question. Before I change the ownership of /media/slavedrive, should hdb1 be mounted there or not?

---

### Post by taurus on 2007-04-17
You can mount /dev/hdb1 anywhere you want (well, not anywhere since there are certain places you shouldn't mount to but that would be another thread, I guess).  Therefore, /media/slavedrive is fine.

---

### Post by Dave54 on 2007-04-17
To clarify what I said:

There are two options.

_Option A:_

1. hdb1 **is** mounted to /media/slavedrive
2. then run:
```
sudo chown -R dave:dave /media/slavedrive
sudo chmod -R 755 /media/slavedrive
ls -la /media
```

_Option B:_

1. hdb1 **is _not_** mounted to /media/slavedrive
2. then run:
```
sudo chown -R dave:dave /media/slavedrive
sudo chmod -R 755 /media/slavedrive
ls -la /media
```



Does it matter which option I take?

---

### Post by taurus on 2007-04-17
If you don't mount your /dev/hdb1, then you can't copy stuff to it.  And you only have to change ownership once for /media/slavedrive.

---

### Post by Dave54 on 2007-04-17
I'm sorry. I'm not sure who, but one of us is not understanding the other.

I know I only have to change ownership once for /media/slavedrive. I haven't done it yet. The reason I haven't done it yet is that I am not sure **whether or not it should be mounted** _before_ changing the ownership.:confused: 

If I still don't understand what you mean, I'll try it without anything mounted.

---

### Post by Larkshall on 2007-04-17
I am a fairly new user, I have Dapper Drake on my Laptop and had Edgy Eft on the Desktop, I have now installed Feisty Fawn on the Desktop. I have been looking at the above postings and they seem very complicated. Is it not easier to use a USB HDD for backup rather than having a slave drive.

After making the mistake of saving my latest files on the master HDD, then formatting and installing Feisty (which lost my latest files), I now save all my data to the USB HDD and can use it with either the Laptop or Desktop. The USB HDD is formatted as FAT32 (it was used with the old Windows XP system).

---

### Post by Dave54 on 2007-04-17
You're right, Larkshall, a usb hdd is oftentimes easier and more versatile, however I'm more of improvising with what I've got.

Thanks for the thought.

---

### Post by Dave54 on 2007-04-17
OK, I went ahead and did
```
sudo chown -R dave:dave /media/slavedrive
sudo chmod -R 755 /media/slavedrive
ls -la /media
```
**without** hdb1 being mounted. "ls -la /media" returned the following:
```
dave@ubuntu:~$ ls -la /media
total 24
drwxr-xr-x  6 root root 4096 2007-04-17 14:33 .
drwxr-xr-x 21 root root 4096 2007-02-17 15:56 ..
lrwxrwxrwx  1 root root    6 2007-02-17 15:15 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-02-17 15:15 cdrom0
lrwxrwxrwx  1 root root    7 2007-02-17 15:15 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-02-17 15:15 floppy0
drwxr-xr-x  2 root root 4096 2007-02-21 11:54 hdb1
drwxr-xr-x  2 dave dave 4096 2007-04-17 14:33 slavedrive

```

I then did "sudo mount -a" which mounted it. I tried to modify files, but got the permission error again.

So, I guess hdb1 should have been mounted **before** changing the permissions. Now I'm not sure what to do. Did I mess something up? How do I undo it? Please help.

---

### Post by Dave54 on 2007-04-17
OK, I figured I could delete the folder and start over again.

I ran the following:
```
sudo umount /media/slavedrive/
sudo rm -r /media/slavedrive/
sudo mkdir /media/slavedrive
sudo mount -a
sudo chown -R dave:dave /media/slavedrive
sudo chmod -R 755 /media/slavedrive
ls -la /media
```
So this time hdb1 was mounted **before** changing the permissions. I modified files and it worked! Problem solved.

---

### Post by Dave54 on 2007-04-17
If someone reads this hoping to set up a slave drive (and access it), this will do it:

First, you need to know what the slave drive is named. This may help:
```
sudo fdisk -l
```
I will assume it's "/dev/hdb1". If it's already mounted, run:
```
sudo umount /media/hdb1
```
Next, make a mount point. I chose "/media/slavedrive"
```
sudo mkdir /media/slavedrive
```
Now run
```
sudo gedit /etc/fstab
```
But you may want to back it up first. If there's a line starting with your slave drive (/dev/hdb1 for me) then delete that line. Replace it with
```
/dev/hdb1                            /media/slavedrive     ext3         defaults                    0  2  
```
But modify your drive and mount point. Save that file and run
```
sudo mount -a
```
to mount your drive.
You have to modify the next line. Replace "dave" with your login name, and change the mount point to your choice again.
```
sudo chown -R dave:dave /media/slavedrive
```
Finally, (modify and) run
```
sudo chmod -R 755 /media/slavedrive
```
and that should be it! You should have full access to your slave drive and it will be automatically mounted each time you boot!

If anyone disagrees with this process, please post.

---

### Post by hunterguy86 on 2007-09-15
[B]I have a 160 gb hd that is formated ntfs. I have files on it that had with windows that I need to keep, (pics, music, ect)

I followed your instructions above but when I ran sudo mount -a, I get the following error:[/B] 

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

[B]
Here is everything I did in terminal:[/B]

lonestar@LONESTAR:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16708   134206978+   7  HPFS/NTFS
lonestar@LONESTAR:~$ sudo umount /media/sdb
umount: /media/sdb: not found
lonestar@LONESTAR:~$ sudo umount /dev/sdb
umount: /dev/sdb: not mounted
lonestar@LONESTAR:~$ sudo mkdir /media/slavedrive
lonestar@LONESTAR:~$ sudo gedit /etc/fstab
lonestar@LONESTAR:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**Here is my fstab file:**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=08e5703d-15d7-47fb-a1df-4920beed23a9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ed78c7a5-481d-4701-87a6-23549ea0f070 none            swap    sw              0       0
/dev/sdb        /media/slavedrive     ext3    defaults      0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

**Thanks for any help that you can provide. **

---

