---
title: "Need help editing /etc/fstab to auto mount NTFS"
date: 2014-01-10
forum: General Help
---

### Post by maxson-chester on 2014-01-10
Hello,

I've got an internal NTFS drive with my media on it, but it needs to either manually mounted or accessed in file manager each time I boot. I'm trying to edit my /etc/fstab file to auto mount the drive system wide on startup, but I'm having trouble figuring out exactly how to do this. 

Here was my attempt, which gave me mount errors on the subsequent boot, so I've deleted it.
```
# NTFS ~ use ntfs-3g for write access (rw)
UUID=F23856003855C3EF Media 1 ntfs-3g auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0
```

Prior to me adding this code (and right now, since I've deleted the attempt), the only UUID's in the fstab.config were my ext4 and swap partitions, both on my primary hard drive.

Here's the relevant blkid for the drive:

```
/dev/sdb1: LABEL="Media 1" UUID="F23856003855C3EF" TYPE="ntfs" 

```

I followed some help examples that I found, but I'm not sure exactly how to make this work.

---

### Post by carl4926 on 2014-01-10
Change the original to

```
UUID=F23856003855C3EF Media 1 ntfs-3g defaults 0 0
```

---

### Post by maxson-chester on 2014-01-10
> **carl4926 said:**
> Change the original to

```
UUID=F23856003855C3EF Media 1 ntfs-3g defaults 0 0
```

I'm getting an error on  boot with "unable to mount drive Media not present or ready" (or something to that effect). I'm guessing that it has to do with the space in the way I originally formatted the drive. Do you know the syntax for adding the space+1?

---

### Post by deadflowr on 2014-01-10
Do you have a place called Media?
Like a folder?
I would think the mountpoint would have a name like /media/storage, or something like that.

---

### Post by carl4926 on 2014-01-10
What I tend to do is use labels
Gparted can add that easily, lets call it STORE

The I create a folder in the root tree eg: /STORE

```
cd /
```
```
sudo mkdir STORE
```
```
sudo chown -R *yourname* /STORE
```
*yourname* without the * and means your login name

Then if sdb is the partition, try this in fstab
```
/dev/sdb /STORE ntfs-3g defaults 0 0
```
reboot

---

### Post by Impavidus on 2014-01-10
The only thing really wrong with your original attempt is that you wrote **Media 1** where you had to specify the mountpoint. Just put in the path of an otherwise empty directory where you want to mount the ntfs drive. Remember to quote it if it contains whitespace. The mount options may not be optimal, but this is of less importance.

---

### Post by oldfred on 2014-01-10
Similar to above. But you do have to have mount point created first.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:


 ** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD

      
 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

### Post by maxson-chester on 2014-01-10
> **oldfred said:**
> Similar to above. But you do have to have mount point created first.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:


 ** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD

      
 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

Looks like that did the trick! I've got a couple of questions: 

Why did the drive auto-mount when I naviagted it with Files, but when a different program attempted to access some data on the drive, it wouldn't auto-mount? 

Also, will does this drive mount during logging into my main admin account, or does it do it on startup, or does it do it on any user log in? I'm trying to figure out if I'll have any problems with the drive not-mounted on different user accounts.

---

### Post by oldfred on 2014-01-10
It should be start-up as it also has to see / & swap at same time.

But default permissions are set in fstab with NTFS and UID=1000 is only first user.

Nautilus mounts it to a default location and set of permissions. Once mounted you cannot mount again. 

I do not know if this is still an issue or not. If Nautilus left panel shows it a second time with a underscore at end that will not work.
 Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

