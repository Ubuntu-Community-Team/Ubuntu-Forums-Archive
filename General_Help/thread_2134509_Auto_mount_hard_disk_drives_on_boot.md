---
title: "Auto mount hard disk drives on boot??"
date: 2013-04-11
forum: General Help
---

### Post by Deucalion29710 on 2013-04-11
Does anybody know how to make a secondary hard drive mount automatically at boot?  I have read many other posts with a similar issue.  I have a 64 GB SSD as my primary and a 250 GB HDD as a secondary.  I just use the secondary for storage purposes.  I have read in the forums that my fstab needs to be edited to have an entry for the hard disk drive.  I am able to edit the file, but nothing has worked.  The output of the drive is as follows:

/dev/sdb1 /media/chris/b5c005c9-ace8-4aaf-a5cd-a3614353a0b1 ext4 rw,nosuid,nodev,uhelper=udisks2 0 0

How do I get this to mount on boot without having to manually click on the hard drive in my file manager?  Could comebody please tell me the exact line in which I need to add to fstab and where to add it in fstab?

Another issue sort of along the same lines is that I have a 500GB My Passport USB hard drive.  Most of the time it mounts at boot but sometimes it does not.  Any ideas???

---

### Post by r.stiltskin on 2013-04-11
It really depends on how you intend to use the disk and how you want to set up its permissions, but this should help you get started.  First create a mount point, where the disk will be located in your file system.

For example:
```
sudo mkdir /mnt/storage
```

Then add to your /etc/fstab (it doesn't really matter where; for convenience just put it at the end of the file and press enter so there's a blank line at the bottom):
```

# /dev/sdb1 250 gb secondary hdd
UUID=b5c005c9-ace8-4aaf-a5cd-a3614353a0b1     /mnt/storage     ext4     uid=1000,gid=1000,umask=007   0  2
```
That will allow only your primary user account and its primary group, which are normally user id 1000 and group id 1000, to read, write and execute any file in that partition.

If you want to easily access that directory from your home directory you can create a soft link like this (assuming your username is chris.):
```

ln -s /mnt/storage /home/chris/storage
``` Then when you click on storage in your home folder it will immediately show the contents of the secondary drive.

If you want to set up different permissions for the files on that disk you can find some explanations in this [tutorial]("http://www.tuxfiles.org/linuxhelp/fstab.html").  Also see the manpages for fstab and mount (in a terminal window run the command "man fstab" or "man mount", without the quotes).

---

### Post by Deucalion29710 on 2013-04-11
> **r.stiltskin said:**
> It really depends on how you intend to use the disk and how you want to set up its permissions, but this should help you get started.  First create a mount point, where the disk will be located in your file system.

For example:
```
sudo mkdir /mnt/storage
```

Then add to your /etc/fstab (it doesn't really matter where; for convenience just put it at the end of the file and press enter so there's a blank line at the bottom):
```

# /dev/sdb1 250 gb secondary hdd
UUID=b5c005c9-ace8-4aaf-a5cd-a3614353a0b1     /mnt/storage     ext4     uid=1000,gid=1000,umask=007   0  2
```
That will allow only your primary user account and its primary group, which are normally user id 1000 and group id 1000, to read, write and execute any file in that partition.

If you want to easily access that directory from your home directory you can create a soft link like this (assuming your username is chris.):
```

ln -s /mnt/storage /home/chris/storage
``` Then when you click on storage in your home folder it will immediately show the contents of the secondary drive.

If you want to set up different permissions for the files on that disk you can find some explanations in this [tutorial]("http://www.tuxfiles.org/linuxhelp/fstab.html").  Also see the manpages for fstab and mount (in a terminal window run the command "man fstab" or "man mount", without the quotes).

I did all of these steps and now it simply tells me that there was an error mounting /mnt/storage.  It gives me the option to skip so that I can boot.  Also the drive no longer shows in file manager.  What did I do inaccurately?  Is it possible that the drive has to be somehow added to /mnt/storage?  This folder shows as empty.

---

### Post by r.stiltskin on 2013-04-11
I can't tell without more information.

First let's verify your uid and gid.  In a terminal, run the following command and look at the output.
```
cat /etc/passwd
```
At or near the end of the output, do you see the following:
chris:x:1000:1000:chris,,,:/home/chris:/bin/bash

Again, I'm assuming that your username is chris.  If not, exactly what do you see there on the line corresponding to your primary user account?  Cut and paste it here.

If we're OK so far, then run, in your terminal window:
```
sudo blkid
```and that should list the UUIDs of all of your disk partitions.  Cut and paste the exact output here.

And finally, use gedit to open /etc/fstab, and cut and paste the exact contents here.

---

### Post by Morbius1 on 2013-04-11
Change this:
```

UUID=b5c005c9-ace8-4aaf-a5cd-a3614353a0b1     /mnt/storage     ext4     uid=1000,gid=1000,umask=007   0  2
```
To this:
```
UUID=b5c005c9-ace8-4aaf-a5cd-a3614353a0b1     /mnt/storage     ext4     defaults,noatime   0  2
```
ext4 doesn't understand uid, gid, and umask options in fstab.

If you run into further problems post the output of the following commands:
```
 sudo blkid -c /dev/null
```
[COLOR=#0000cd]***EDIT**: Come to think of it you might want to run the "sudo blkid -c /dev/null" command first anyway just to make sure that the UUID number is correct and it is in fact ext4.*[/COLOR]
```
cat /etc/fstab
```

---

### Post by r.stiltskin on 2013-04-11
> **Morbius1 said:**
> Change this:
ext4 doesn't understand uid, gid, and umask options in fstab.

Good to know!  :)

But with a non-home mount point, won't "defaults" limit write access to root?

---

### Post by Deucalion29710 on 2013-04-11
> **r.stiltskin said:**
> I can't tell without more information.

First let's verify your uid and gid.  In a terminal, run the following command and look at the output.
```
cat /etc/passwd
```
At or near the end of the output, do you see the following:
chris:x:1000:1000:chris,,,:/home/chris:/bin/bash

Again, I'm assuming that your username is chris.  If not, exactly what do you see there on the line corresponding to your primary user account?  Cut and paste it here.

If we're OK so far, then run, in your terminal window:
```
sudo blkid
```and that should list the UUIDs of all of your disk partitions.  Cut and paste the exact output here.

And finally, use gedit to open /etc/fstab, and cut and paste the exact contents here.

OK I was able to verify the username.  blkid yielded:

/dev/sda1: UUID="9d393b75-65d8-41bc-902b-53776419fac0" TYPE="ext4" 
/dev/sda5: UUID="e38363c5-8c4a-4176-bf6c-acc56781c35c" TYPE="swap" 
/dev/sdb1: UUID="b5c005c9-ace8-4aaf-a5cd-a3614353a0b1" TYPE="ext4" 
/dev/sdc1: LABEL="My Passport" UUID="46C07088C070804B" TYPE="ntfs"

---

### Post by Morbius1 on 2013-04-11
@**r.stiltskin**

If it is ext4 the ownership and permissions are contained within the metadata of the files themselves. On a newly formated ext4 partition it will mount to owner = root and perms=755. You can't change that in fstab. You have to use chown / chmod after the partition is mounted to change permissions.

But since he's already been using the partition I'm guessing he's already altered permissions so he can access it they way he wants. Once that is done it would carry those same permissions if he handed the disk to me and I installed it and mounted it on my own system.

---

### Post by Deucalion29710 on 2013-04-11
> **Morbius1 said:**
> Change this:
```

UUID=b5c005c9-ace8-4aaf-a5cd-a3614353a0b1     /mnt/storage     ext4     uid=1000,gid=1000,umask=007   0  2
```
To this:
```
UUID=b5c005c9-ace8-4aaf-a5cd-a3614353a0b1     /mnt/storage     ext4     defaults,noatime   0  2
```
ext4 doesn't understand uid, gid, and umask options in fstab.

If you run into further problems post the output of the following commands:
```
 sudo blkid -c /dev/null
```
[COLOR=#0000cd]***EDIT**: Come to think of it you might want to run the "sudo blkid -c /dev/null" command first anyway just to make sure that the UUID number is correct and it is in fact ext4.*[/COLOR]
```
cat /etc/fstab
```

The results of this is now it will boot without error but the drive does not appear in file manager and does not mount.  We're getting somewhere.

---

### Post by Morbius1 on 2013-04-11
Does it show up as mounted in the output of this command:
```
mount
```
If it does not post the output of this command:
```
 cat /etc/fstab
```

---

### Post by r.stiltskin on 2013-04-11
The drive shouldn't appear as a separate drive in file manager.  But you should see its contents in /mnt/storage (and in /home/chris/storage if you created the soft link).

I think the only step that remains to be done is this:
```

sudo chown chris:chris /mnt/storage
```
to allow yourself to freely write to that folder.

---

### Post by r.stiltskin on 2013-04-11
@Morbius1:
Thanks for clearing up my confusion.

---

### Post by Deucalion29710 on 2013-04-12
> **Morbius1 said:**
> Does it show up as mounted in the output of this command:
```
mount
```
If it does not post the output of this command:
```
 cat /etc/fstab
```


not sure where you mean to place "mount" but the output of fstab is:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=9d393b75-65d8-41bc-902b-53776419fac0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e38363c5-8c4a-4176-bf6c-acc56781c35c none            swap    sw              0       0
# /dev/sdb1 250 gb secondary hdd
UUID=b5c005c9-ace8-4aaf-a5cd-a3614353a0b1     /mnt/storage     ext4     defaults,noatime   0  2



I did chown for the directory.  The 250GB drive still shows on shortcuts on my AWN but when I click it now it fails to mount.

---

### Post by r.stiltskin on 2013-04-12
Just type **mount** in your terminal & post the output.

---

### Post by Deucalion29710 on 2013-04-12
mount yielded:

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sdb1 on /mnt/storage type ext4 (rw,noatime)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfsd-fuse on /home/chris/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=chris)
/dev/sdc1 on /media/chris/My Passport type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfsd-fuse on /root/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)

---

### Post by r.stiltskin on 2013-04-12
According to that it is mounted.  And yet you say that if you do
**ls /mnt/storage**
there is nothing?

---

### Post by Deucalion29710 on 2013-04-12
> **r.stiltskin said:**
> According to that it is mounted.  And yet you say that if you do
**ls /mnt/storage**
there is nothing?


[I] I do get my folder names from within the drive

[/I]Apk  Images  Kernels  lost+found  Misc  Screenlets  Themes  Untitled Folder

---

### Post by Deucalion29710 on 2013-04-12
OK it seems to me that it simply changed the location in which it mounts from.  Is there a way to make this show once again as a hard drive in Nautilus?

---

### Post by r.stiltskin on 2013-04-12
> **Deucalion29710 said:**
> OK it seems to me that it simply changed the location in which it mounts from. 

No.  It also changed the *way* that it's mounted.  Now it's automatically mounted when you boot, just like your primary hard disk.  Isn't that what you wanted?

> **Deucalion29710 said:**
> Is there a way to make this show once again as a hard drive in Nautilus?

I can't swear to it, but I don't think so.  The drives listed under "Devices" are, I believe, the ones that are detected but NOT automatically mounted.  They are devices that are not (yet) part of your file system.

If you created the symbolic link as I mentioned in Post #2, you should have a "storage" folder listed in your Home folder that brings you directly to it.

Also, you can add a bookmark to it on the Nautilus sidebar, below the Devices section.  Just open the /mnt/storage folder in Nautilus, and then click on Bookmarks/Add Bookmark.

And by the way, if you want to subdivide it into, say, a "Music" folder and a "Video" folder, etc., you can simply create those folders in your storage folder, and add individual bookmarks to each of them by the same process.

---

### Post by Deucalion29710 on 2013-04-12
> **r.stiltskin said:**
> No.  It also changed the *way* that it's mounted.  Now it's automatically mounted when you boot, just like your primary hard disk.  Isn't that what you wanted?



I can't swear to it, but I don't think so.  The drives listed under "Devices" are, I believe, the ones that are detected but NOT automatically mounted.  They are devices that are not (yet) part of your file system.

If you created the symbolic link as I mentioned in Post #2, you should have a "storage" folder listed in your Home folder that brings you directly to it.

Also, you can add a bookmark to it on the Nautilus sidebar, below the Devices section.  Just open the /mnt/storage folder in Nautilus, and then click on Bookmarks/Add Bookmark.

That's cool and it is what I wanted.  Now I'm just taking care of broken links to the original drive on Avant and Screenlets.  May be a few other shortcuts to the original.  Is there a way to place a shortcut to "storage" in my home folder?  This would give me an alternate shortcut on AWN.

---

### Post by Deucalion29710 on 2013-04-12
By the way you guys are all great.  Thanks to all who have directed me for your efforts and patients.

---

### Post by r.stiltskin on 2013-04-12
> **Deucalion29710 said:**
>  Is there a way to place a shortcut to "storage" in my home folder?  This would give me an alternate shortcut on AWN.
Isn't it already there?  That's what I was suggesting in post #2:

```
ln -s /mnt/storage /home/chris/storage
```
And if you want you can create symbolic links to any sub-folders of storage as well.

And you can add individual bookmarks (on the Nautilus sidebar) to any of the sub-folders of storage.

---

### Post by Deucalion29710 on 2013-04-12
Awesome.  Thanks for your help.  I guess the way I need to remedy the shortcuts menu on awn is to remove and add it back.  Possibly that could refresh the current config.  Thanks again.

---

