---
title: "Auto Mount 2nd IDE hard drive"
date: 2008-04-21
forum: General Help
---

### Post by mpc350 on 2008-04-21
I have 2 drives... one for the OS, the other as a storage drive for music.  The music drive does not mount automatically, so when I open Rhythmbox, it fails to find the files.  So...
A: How do I make the auto drive auto mount?
B: How do I make my music player access this drive

I can find the drive easily enough and manually mount it, but would like it to just show up on the desktop when I boot.

Thanks
Matt

---

### Post by Rocket2DMn on 2008-04-21
You will need to add an fstab entry (or fix one that isn't right), please post
```
sudo fdisk -l
cat /etc/fstab
ls -l /dev/disk/by-uuid
```
Let me know which device is your second disk if it's not obvious.

---

### Post by mpc350 on 2008-04-21
> **Rocket2DMn said:**
> You will need to add an fstab entry (or fix one that isn't right), please post
```
sudo fdisk -l
cat /etc/fstab
ls -l /dev/disk/by-uuid
```
Let me know which device is your second disk if it's not obvious.
here are the results of the fdisc check:  the hdf 20.5gb volume is the one I want to automount.

Disk /dev/hde: 9115 MB, 9115361280 bytes
255 heads, 63 sectors/track, 1108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9aed9ae

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        1055     8474256   83  Linux
/dev/hde2            1056        1108      425722+   5  Extended
/dev/hde5            1056        1108      425691   82  Linux swap / Solaris

Disk /dev/hdf: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1        2495    20041056   83  Linux

---

### Post by Rocket2DMn on 2008-04-21
I need the output of the other 2 commands as well
```
cat /etc/fstab
ls -l /dev/disk/by-uuid
```

---

### Post by mpc350 on 2008-04-21
> **Rocket2DMn said:**
> I need the output of the other 2 commands as well
```
cat /etc/fstab
ls -l /dev/disk/by-uuid
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde1
UUID=5df7ea7b-4f1d-4863-8922-b0572f711c19 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hde5
UUID=6cdedc83-8f45-45fa-bbea-41a6a788ff84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


and....


total 0
lrwxrwxrwx 1 root root 10 2008-04-21 18:38 5df7ea7b-4f1d-4863-8922-b0572f711c19 -> ../../hde1
lrwxrwxrwx 1 root root 10 2008-04-21 18:38 6cdedc83-8f45-45fa-bbea-41a6a788ff84 -> ../../hde5
lrwxrwxrwx 1 root root 10 2008-04-21 18:38 8d336e4d-412a-40b9-a340-0620ec60ce28 -> ../../hdf1


Thanks for your quick replies!

---

### Post by lord gold on 2008-04-21
sorry dude, this isn't a reply to your post, im actually trying to get help from anyone. all im trying to do is post on something that i need help with, but the way that you did it/ so that everyone can see it and have the ability to reply. im a total newbee- 12 minutes ago. no forum experience ever. any help would be greatly appreciated. thanks.

---

### Post by Rocket2DMn on 2008-04-21
OK, let's add the fstab entry for it.  First create the mount point, you can change if it you'd like, just make sure it is changed in fstab, too:
```
sudo mkdir /media/music
gksudo gedit /etc/fstab
```
Add this line to the bottom:
```
UUID=8d336e4d-412a-40b9-a340-0620ec60ce28 /media/music ext3 defaults 0 0
```
You should now be good to go, you can mount the drive without rebooting by running
```
sudo mount -a
```
If you haven't already, you need to chown the files on the drive
```
sudo chown -R yourusername:yourusername /media/music
```

---

### Post by Rocket2DMn on 2008-04-21
> **lord gold said:**
> sorry dude, this isn't a reply to your post, im actually trying to get help from anyone. all im trying to do is post on something that i need help with, but the way that you did it/ so that everyone can see it and have the ability to reply. im a total newbee- 12 minutes ago. no forum experience ever. any help would be greatly appreciated. thanks.

Go to the Absolute Beginner Forum at [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)
then hit New Thread near the upper left side of the page, above the Sticky Threads and Announcement about malicious commands.

---

### Post by mpc350 on 2008-04-22
Thank you so much.   I'll post the results shortly.

Matt

---

### Post by mpc350 on 2008-04-22
So I made the changes, and restarted.  The disc did not mount and I got this error message at startup:

[Users $HOME/.dmrc file is being ignored.  THis prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  Users $HOME directory should be owned by user and not writeable by other users.]

Any help would be appreciated.

Thanks.

Matt

---

### Post by mpc350 on 2008-04-22
Also, the drive hdf is now not showing up when I go to filesystem (from the drop down menu)

Matt

---

### Post by Rocket2DMn on 2008-04-22
That's rather strange, I'm going to have you post the output of those commands again, to see if they changed.  A few other commands are also listed
```
sudo fdisk -l
cat /etc/fstab
ls -l /dev/disk/by-uuid
ls -l ~/.dmrc
ls -l /home
```

---

### Post by mpc350 on 2008-04-22
Disk /dev/hde: 9115 MB, 9115361280 bytes
255 heads, 63 sectors/track, 1108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9aed9ae

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        1055     8474256   83  Linux
/dev/hde2            1056        1108      425722+   5  Extended
/dev/hde5            1056        1108      425691   82  Linux swap / Solaris

Disk /dev/hdf: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1        2495    20041056   83  Linux



and...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde1
UUID=5df7ea7b-4f1d-4863-8922-b0572f711c19 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hde5
UUID=6cdedc83-8f45-45fa-bbea-41a6a788ff84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
UUID=8d336e4d-412a-40b9-a340-0620ec60ce28 /media/music ext3 defaults 0 0



and...

total 0
lrwxrwxrwx 1 root root 10 2008-04-21 22:20 5df7ea7b-4f1d-4863-8922-b0572f711c19 -> ../../hde1
lrwxrwxrwx 1 root root 10 2008-04-21 22:20 6cdedc83-8f45-45fa-bbea-41a6a788ff84 -> ../../hde5
lrwxrwxrwx 1 root root 10 2008-04-21 22:20 8d336e4d-412a-40b9-a340-0620ec60ce28 -> ../../hdf1



and...

-rw------- 1 mattc mattc 28 2008-04-21 18:39 /home/mattc/.dmrc


and...

total 4
drwxr-xrwx 33 mattc mattc 4096 2008-04-21 22:21 mattc


hope this helps.

Matt

---

### Post by mpc350 on 2008-04-22
Dont know if this makes a difference but the line you had me insert in the fstab file makes reference to ext3 filestructure...  I believe I formatted that drive in ext2.  Just an observation.

Matt

---

### Post by Rocket2DMn on 2008-04-22
OK, start with
```
chmod 644 ~/.dmrc
```
That will fix the first error.  Also, your $HOME directory should not be writable by World, so run
```
chmod 755 ~
```
I'm not sure what you mean when you say hdf is not showing from the drop down menu in filesystem?  It should be mounted at /media/music
Since we made changes to your home folder, let's just reboot the system.  When you get back in, if the drive is not listed anywhere, post the output of
```
mount
sudo mount -a
```
If needed, we can add some more options to fstab.  Let me know if you can see the files in /media/music and if you can read/write to that mount point.

---

### Post by mpc350 on 2008-04-22
/dev/hde1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)


and...

mount: wrong fs type, bad option, bad superblock on /dev/hdf1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I mentioned filesystem from the dropdown... I meant Places>Filesystem, where I usually find mounted drives, etc.

---

### Post by Rocket2DMn on 2008-04-22
OK, because fdisk said the System was "Linux", I assumed ext3.  Is it not?  If it IS, then maybe you need to check the partition for errors using
```
sudo fsck /dev/hdf1
```
(this could take awhile)
Otherwise you can try changing the fstab entry to have the filesystem as "auto", so the line would look like
```
UUID=8d336e4d-412a-40b9-a340-0620ec60ce28 /media/music auto defaults 0 0
```
If you know for sure what the filesystem is, please let me know and we can set the entry appropriately.  You can also try mounting it manually (assuming ext3) with
```
sudo mount -t ext3 /dev/hdf1 /media/music
```
Post errors here (include the command, too, just copy and paste the works).

---

### Post by mpc350 on 2008-04-22
When  I reformatted that drive, I made it ext2 (it was the default)  should I amend the fstab file with ext2 written in?

---

### Post by Rocket2DMn on 2008-04-22
Yes.  ext3 would have been preferable since it has journaling (it's essentially ext2 + journaling).  All that means is that if the partition is unmounted improperly and it is ext3, you won't have to fsck the partition.  So if it does get unmounted badly, you will have to use the fsck command before you can mount it again.

---

### Post by mpc350 on 2008-04-22
Just rebooted and everything is great!  

My wife thanks you too... She knows I would have been consumed by this for the next 3 days.

It's people like you that make this a great forum and great community.

Matt

---

### Post by pluckypigeon on 2008-11-14
have a look at this if you are stuck!

[http://ubuntuforums.org/showthread.php?p=6177625#post6177625](http://ubuntuforums.org/showthread.php?p=6177625#post6177625)

---

### Post by dmanbluesfreak on 2008-11-17
How would I go about mounting my sda1 drive?

Here's the outputs to those 3 commands:
[I]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5518f83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58868   472856186    7  HPFS/NTFS
/dev/sda2           58869       60676    14522760   83  Linux
/dev/sda3           60677       60801     1004062+   5  Extended
/dev/sda5           60677       60801     1004031   82  Linux swap / Solaris

----------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0b6a2a27-12f6-43e2-8092-00a2c5aaafa1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6e14162d-0ebf-4668-aeac-9a7333556ef1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

-----------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0b6a2a27-12f6-43e2-8092-00a2c5aaafa1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6e14162d-0ebf-4668-aeac-9a7333556ef1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[/I]

What commands do I need to have this mount automatically (the whole drive, not just music)?

---

### Post by dmanbluesfreak on 2008-11-17
Wait, sorry for the double post, but I just clicked on PluckyPidgeon's link, and I'm going to try that first.

---

### Post by Arup on 2008-11-18
pysdm from the repos is fully GUI and after install you can find it at system>administration>storage device manager. Its an excellent safe way for novices and advanced users alike, one that I highly recommend.

---

### Post by dmanbluesfreak on 2008-11-18
> **Arup said:**
> pysdm from the repos is fully GUI and after install you can find it at system>administration>storage device manager. Its an excellent safe way for novices and advanced users alike, one that I highly recommend.


Yep, I just saw that at the link in the above post, thanks!:KS

---

