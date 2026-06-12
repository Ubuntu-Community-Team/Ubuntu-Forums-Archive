---
title: "Ubuntu won't let me copy anything to/from my computer from a removable drive..."
date: 2007-09-01
forum: General Help
---

### Post by hyrule_man on 2007-09-01
I have my Memory Stick PRO Duo in there, and I'm trying to copy some music onto it. But it says I don't have permission to . WTF?

---

### Post by splintercellguy on 2007-09-01
What filesystem? If NTFS, sudo apt-get install ntfs-config.

---

### Post by hyrule_man on 2007-09-01
I'm not too sure.. I think FAT, because I last formatted it with my PSP...

---

### Post by Benjamin G on 2007-09-01
I don't mean to be pedantic, but is the device mounted?  And if so, what are the permissions for it?

---

### Post by hyrule_man on 2007-09-01
Forgive my 100% noobness, but what exactly does mounted mean? I've heard the trem like 100,000,000 times, but dunno what it means....

---

### Post by Benjamin G on 2007-09-01
My understanding of the term is limitted to it's practical use - so someone else could probably give you a more technical answer!  Basically, a filesystem has to "mounted" at a "mount point" before the system can access it.  Try right-clicking on icon, and see if it gives you an option to mount/unmount it.

---

### Post by merlinus on 2007-09-01
Basically, in ubuntu a drive and/or partition has to be mounted before you can do anything with it.

You might check System/Preferences/Removable Drives and Media to make sure the correct boxes are ticked.

Then try re-inserting the usb drive.

-merlin

---

### Post by Benjamin G on 2007-09-01
Once it is mounted, check the properties to find it's mount point.  Then run the following command at the command line:
```
ls -l [mount point]
```
replacing [mount point] with the mount point for the device.

And copy the resulting output to this thread.

---

### Post by hyrule_man on 2007-09-01
Oh, ok, I just figured out what mounting/unmounting is. Anywho, yes. Its mounted. But When I go to properties, I try to change it to read+write, but it keeps giving me a "This disk is read-only" error... What the heck?

---

### Post by hyrule_man on 2007-09-01
Just messed around in the removable drives and media. Didn't fix a thing....

---

### Post by Benjamin G on 2007-09-01
Ok, try running the following command, with <mount point> replaced as before.
```
chmod +rwx <mount point>
```
If that doesn't work, try the same but with "sudo" before it.

---

### Post by merlinus on 2007-09-01
IIRC, chmod and chown only work with linux-formatted partitions, files, and drives.

Fat32 permissions need to be set at time of mounting, or in /etc/fstab.

NTFS uses ntfs-3g.

-merlin

---

### Post by hyrule_man on 2007-09-01
So.. What do I do? I put that in the terminal, and I get this:

david@david-desktop:~$ /etc/fstab
bash: /etc/fstab: Permission denied

---

### Post by Benjamin G on 2007-09-01
You need
```
more /etc/fstab
```
"more" is a command which prints the contents of /etc/fstab (a file) to the screen.

---

### Post by hyrule_man on 2007-09-01
I come up with this:




david@david-desktop:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=181b849a-ee4a-49b0-9151-c6e82f51488a /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=1142c353-c81c-4bcb-a8bc-4802fd9540d5 none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Benjamin G on 2007-09-01
Sometimes usb devices mount in mtab instead of fstab.  What are the results of```
more /etc/mtab
```?

---

### Post by hyrule_man on 2007-09-01
david@david-desktop:~$ more /etc/mtab
/dev/hda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdd /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=07
7 0 0

---

### Post by Benjamin G on 2007-09-01
> **hyrule_man said:**
> 
/dev/sdd /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=07
7 0 0
I'm guessing that this is the device you are after.  It's mounted at /media/disk.  What is the result of the following command?
```
ls -l /media
```
And what happens if you try you following
```
cd /media/disk
```

---

### Post by hyrule_man on 2007-09-01
david@david-desktop:~$ ls -l /media
total 12
lrwxrwxrwx 1 root  root    6 2007-08-29 10:18 cdrom -> cdrom0
drwxr-xr-x 2 root  root 4096 2007-08-29 10:18 cdrom0
drwx------ 6 david root 4096 1969-12-31 19:00 disk
drwx------ 2 root  root 4096 2007-09-01 18:35 GARY'S IPOD





and




david@david-desktop:~$ cd /media/disk
david@david-desktop:/media/disk$ 




NOTE: That GARY'S IPOD is my friend's iPod Video he just plugged into my PC today.

---

### Post by hyrule_man on 2007-09-02
Bump.

---

### Post by merlinus on 2007-09-02
```

gksudo nautilus

```

Navigate to Places/Computer/File System/media.  Right-click on the disk folder, select Properties and then Permissions.  Change Others to Create and Delete Files.

Then restart.

-merlin

---

### Post by hyrule_man on 2007-09-02
Heres what I get when I go to the properties:


[IMG]http://i95.photobucket.com/albums/l121/geckron/Screenshot.png[/IMG]


Then when I try to change any of the permissions:


[IMG]http://i95.photobucket.com/albums/l121/geckron/Screenshot-1.png[/IMG]

---

### Post by hyrule_man on 2007-09-02
*sigh* Bump.....

---

### Post by merlinus on 2007-09-02
From what I see, david - David Shook is the owner and has create-and-delete-files privileges.

If this is your user id, then you should have no problems doing this.

If not, then login as him and see what happens.

-merlin

---

### Post by hyrule_man on 2007-09-02
Well, I am David. I'm the only person who uses the PC.

---

### Post by Total_Biscuit on 2007-09-02
> **hyrule_man said:**
> Well, I am David. I'm the only person who uses the PC.

Why do you need to change the permissions?  The disk is read/write for the user david.  Of course, as a user you will not be able to change the permissions either for root or for other users.

Has that memory stick got one of those read only switches and is it set to read only?

---

### Post by hyrule_man on 2007-09-02
Wait, I'm David... So wouldn't that make me ABLE to change the permissions...?

---

### Post by hyrule_man on 2007-09-02
*Cries*

---

### Post by david_2001 on 2007-09-02
> **hyrule_man said:**
> Wait, I'm David... So wouldn't that make me ABLE to change the permissions...?
The screenshots show that you have read/write permissions to the memory card already.  Did you check that little read-only switch on the memory card itself yet?

---

