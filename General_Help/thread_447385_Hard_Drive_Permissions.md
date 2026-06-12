---
title: "Hard Drive Permissions"
date: 2007-05-17
forum: General Help
---

### Post by viergeame on 2007-05-17
A few weeks ago I started having problems with the permissions on my windows drive and my external drive.  At first I lost write permission on both and I got suggestions on things I could do to fix it but nothing seemed to work so I gave up on it.  Now for some reason I can't even access my windows drive without a password and my external drive says it's mounted but when I click on it no files are shown.  I've looked up all sorts of solutions and it is seeming like everything I do is just breaking something different.  I can't figure out what I'm doing wrong.

---

### Post by dfreer on 2007-05-18
First, we'll need a little bit more info. could you post your /etc/fstab and /etc/mtab files please?
Also, are you using NTFS on either drive? If so, do you have the NTFS3G driver installed?

EDIT: Also, do both drives work in windows?

---

### Post by viergeame on 2007-05-18
Here is my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=8e4ea2ff-3a73-4236-a288-1119db0c1ffb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=cc1856da-36b5-48b0-b44e-6feb4c6b4759 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/FAT32  vfat  noauto,users,rw,exec   1  0

Here is my /etc/mtab

/dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

One of my drives is NTFS and the other is FAT32.  I'm not sure if I have that NTFS driver installed.  I don't think I do but the drive worked fine and had all the permissions a few weeks ago and I haven't changed anything since then.  Yes, both drives do work in Windows.

---

### Post by dfreer on 2007-05-19
you'll need to install the NTFS3G driver in order to write to NTFS drives (reading should be fine). I'll get ya more info when I'm not so sleepy :(

---

### Post by viergeame on 2007-05-19
I will get that installed and see how that works.  Everything worked fine (reading and writing) a few weeks ago though without that driver, so I didn't know I needed it.  Is there something that simple to solve the problems with the FAT32?

---

### Post by tommcd on 2007-05-19
You should not need the NTFS3G to read and write to a fat32 partition. Can you cd into the /media/FAT32  directory and type "ls -al" to see what the permissions are? Or right click on the directory to check the permissions. You should see read and write for the owner. If not, try "sudo chown -R your_user_name:users /media/FAT32" and see if you can read and write to it without a password. This should return ownership of /media/FAT32 to you.

---

### Post by dfreer on 2007-05-19
Also post the outputs of l*s -al /media/FAT32* and *ls -l /media*. 

Also, you need to check up on this line, specifically this part:
```
/dev/sda1 /media/FAT32 vfat noauto,users,rw,exec ***_1_*** 0
```
I'm pretty sure that should be a zero, but I can't remember what it does off the top of my head so I could be wrong. Check it out.

---

### Post by viergeame on 2007-05-19
I installed that NTFS driver and when I looked at the properties it gave me a drop down menu to change the permissions but when I selected read and write it came up with an error saying I couldn't do that.  I decided to restart since that seems to fix lots of things and now I don't even get the menu anymore and it says everything belongs to root again.  And the FAT32 drive won't mount anymore.  When I try to mount it I get an error saying "invalid mount option when trying to mount FAT32"

Here are the outputs you need.

nikki@nikki:~$ ls -l /media
total 36
lrwxrwxrwx 1 root  root      6 2007-04-12 16:20 cdrom -> cdrom0
drwxr-xr-x 2 root  root   4096 2007-04-12 16:20 cdrom0
drwxr-xr-x 2 root  root   4096 2007-04-12 16:20 cdrom1
dr-xr-xr-x 1 root  root  16384 2007-05-15 03:00 disk
drwxr-xr-x 2 root  root   4096 2007-05-10 23:54 external
drwxr-xr-x 2 nikki users  4096 2007-05-16 20:15 FAT32
lrwxrwxrwx 1 root  root      7 2007-04-12 16:20 floppy -> floppy0
drwxr-xr-x 2 root  root   4096 2007-04-12 16:20 floppy0


nikki@nikki:~$ ls -al /media/FAT32
total 8
drwxr-xr-x 2 nikki users 4096 2007-05-16 20:15 .
drwxr-xr-x 8 root  root  4096 2007-05-19 13:07 ..


I changed that to a 0 and nothing seems to have happened, good or bad.

I'm beginning to wonder if a colony of computer-hating gnomes has taken up residence in my tower.  Every time one thing seems fixed something else breaks, but at least the things breaking are fairly minor compared to some of the problems I have seen other people have....

---

### Post by tommcd on 2007-05-19
I assume your username is nikki. If so then did you try "sudo chown -R nikki:users /media/FAT32" like I suggested? If not, then try it. Or change "nikki" to whatever your username is.

---

### Post by viergeame on 2007-05-19
I tried chown and nothing changed.  The FAT32 drive won't actually mount now, but I tried that on the NTFS drive and it didn't do anything.  Also, when I first started having this problem a few weeks ago that is what a friend suggested and it didn't do anything then either.  Usually my solution to these things is just to reformat and try again, but I don't want to resort to that again since I don't really learn anything that way.

---

### Post by CaveRat on 2007-05-20
> **tommcd said:**
> I assume your username is nikki. If so then did you try "sudo chown -R nikki:users /media/FAT32" like I suggested? If not, then try it. Or change "nikki" to whatever your username is.

Hey thanks for the info. This little glitch has been plaguing me for some time now.  I now have user privileges on an added drive that would not allow me to write to it due to root ownership. I see another Tomboy note being added here.

---

