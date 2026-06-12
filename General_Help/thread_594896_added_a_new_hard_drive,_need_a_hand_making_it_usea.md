---
title: "added a new hard drive, need a hand making it useable..."
date: 2007-10-28
forum: General Help
---

### Post by Nathan Otis on 2007-10-28
I have physically installed an old HDD in my Gutsy machine for a little extra room. I need some help getting it working correctly.

I have gotten and run Gparted and the drive is formatted for use in Ubuntu. At this point, it doesn't auto mount and I can't write to it. The error message says...

> Error while copying to "/media/disk". You do not have permissions to write to this folder.

I've searched around but haven't found information I feel comfortable executing in my terminal. What follows are the output from commands I think will help fix this (as gleaned from other threads):


otis@otis-desktop:~$ sudo fdisk -l
[sudo] password for otis:

Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003bc42

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        2040     1028160   82  Linux swap / Solaris
/dev/hda3            2041        7299    42242917+  83  Linux

Disk /dev/hdb: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3328    26732128+  83  Linux
otis@otis-desktop:~$ 

********************

otis@otis-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=52f10116-e54d-4ae7-816b-c3bd8fd115ca / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=34507C44507C0EBC /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=cecf85c4-f552-4967-b9f8-6af336206385 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0otis@otis-desktop:~$

********************

otis@otis-desktop:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hdb1 on /media/disk type ext3 (rw,nosuid,nodev)
otis@otis-desktop:~$

********************

Do I need to bust out the LiveCD to get it going or can it be done (as I'm sure it can) from within Gutsy?

Thanks in advance.
n.

---

### Post by Jose Catre-Vandis on 2007-10-28
Do the following:

```
sudo mkdir /media/HDD2
```
(you can choose what youwant to call it!)

then

```
sudo mount -t ext3 /dev/hdb1 /media/HDD2
```

HDD2 should appear!

for permanent mount:

```
sudo nano /etc/fstab
```

add the line:
```
/dev/hdb1     /media/HDD2    ext3    defaults     0   2  
```

save and reboot.

---

### Post by Nathan Otis on 2007-10-28
That seemed to work (HDD2 is now mounting under "/media"), but it is still unwritable. I "... do not have permissions to write to this folder." I made a shortcut on the desktop (slave to the gui) and theres a lock on it.

Also, I notice it still shows up as "25.5 GB Volume" under /computer. I can mount it there, but it shows as "disc" and is unwritable.

---

### Post by Jose Catre-Vandis on 2007-10-28
Open Nautilus as root, and change permissions for the drive to your user.

or from the command line:
```
sudo chown -R  yourusername /media/HDD2 
sudo chmod 664 -R /media/HDD2
```
(664 gives owner and group read/write and others read only)
(777 makes it wide open for all to read/write)

---

### Post by Nathan Otis on 2007-10-28
That's done the trick. I assume that will persist after reboot.

Thank you.
I love this forum.
n.

---

### Post by Jose Catre-Vandis on 2007-10-28
yes, no reason why it shouldn't persist.

Why there isn't a wizard in Ubuntu to handle this I do not know, adding or changing hardware in Ubuntu whilst do-able comes with little direct support unless you know what you are doing. Much the same with networks :)

Happy to help :)

---

### Post by Nathan Otis on 2007-10-28
I'm baaaack. (That didn't take long)

I need a little help understanding what is happening because it doesn't seem right...

The new HDD2 is mounted under /media. When I open the drive (it looks like a folder), the status bar says there are 4gb free. This is the same number given in any other folder on my primary Ubuntu drive.

I have moved several gig of files to HDD2 and the number does not change on either the primary or the secondary (HDD2)

Also, HDD2 is still seen as 25.5GB Volume in "Computer", but does not show up as a hard drive with the name HDD2 (I assume this is because of how it's mounted to /media, but it's a little confusing. I'd expect to see a HDD show up as a HDD...

Oh, and I've gone to Gparted and it shows HDD2 almost completely empty while my primary (that I've moved files off of) is still just about maxed.

Please clarify. Thanks.
n.

---

### Post by Nathan Otis on 2007-10-28
Sorry for the bump. I'm a little anxious. Lots of downloading to do, very little space to do it in...
n.

---

### Post by Jose Catre-Vandis on 2007-10-28
Have you rebooted yet? and by that i mean a shutdown, switch off, walk away, walk back  and start up again.

also please post an output of ```
sudo fdisk -l
``` again along with ```
df -Th
```

---

### Post by Nathan Otis on 2007-10-28
I have rebooted. I did it again just now and even turned the monitor off for good measure! Fed the dogs, made a sandwich, turned the PC back on. No changes. HDD2 is still mounting under /media, but the actual space isn't there (or it isn't showing).

The output you requested:

otis@otis-desktop:~$ sudo fdisk -l
[sudo] password for otis:

Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003bc42

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+  83  Linux
/dev/hda2            1913        2040     1028160   82  Linux swap / Solaris
/dev/hda3            2041        7299    42242917+  83  Linux

Disk /dev/hdb: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3328    26732128+  83  Linux
otis@otis-desktop:~$ 

********************

otis@otis-desktop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda3     ext3     40G   31G  7.3G  81% /
varrun       tmpfs    253M   92K  252M   1% /var/run
varlock      tmpfs    253M     0  253M   0% /var/lock
udev         tmpfs    253M   88K  252M   1% /dev
devshm       tmpfs    253M     0  253M   0% /dev/shm
lrm          tmpfs    253M   35M  218M  14% /lib/modules/2.6.22-14-386/volatile
otis@otis-desktop:~$

---

### Post by Jose Catre-Vandis on 2007-10-29
Yeah, it's not showing the mount in df. Would have expected something like this:
##############################################
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3     19G   11G  7.0G  60% /
varrun       tmpfs    252M  188K  252M   1% /var/run
varlock      tmpfs    252M  4.0K  252M   1% /var/lock
udev         tmpfs    252M  128K  252M   1% /dev
devshm       tmpfs    252M     0  252M   0% /dev/shm
lrm          tmpfs    252M   19M  234M   8% /lib/modules/2.6.15-28-386/volatile
/dev/hdb1     ext3    367G  156G  193G  45% /media/HDD2
###############################################

Your second hard drive will always be mounted in /media given the way we have configured it. Why does hdb1 have a boot flag?  Is hdb formatted to ext3? Worth a try reformatting hdb to ext3 using Gparted and removing the boot flag whilst you are at it.

reaching the limits of my understanding now :)

---

### Post by Nathan Otis on 2007-10-29
Ok, let's address one thing at a time, I guess... Let's see if we can get the secondary drive working so I can clear space on my primary. Then I can worry about where it's mounting...

Here's new output... it's most definately formated ext3 and the boot flag is gone:

otis@otis-desktop:~$ sudo fdisk -l
[sudo] password for otis:

Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003bc42

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+  83  Linux
/dev/hda2            1913        2040     1028160   82  Linux swap / Solaris
/dev/hda3            2041        7299    42242917+  83  Linux

Disk /dev/hdb: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3328    26732128+  83  Linux
otis@otis-desktop:~$

---

### Post by Jose Catre-Vandis on 2007-10-31
Hi Nathan Otis, have you got any where with your disk size issues?

---

### Post by Nathan Otis on 2007-10-31
As it happens, I made a Gparted CD last night and figured everything out on my primary. I cannibalized my windows partition (I'm all Linux now, better start learning that command line!). Here's a question related to that...

Should the swap file be at the front or the back of the drive? I see I can move it with Gparted... Is there a better choice or does it matter?

With regards to my newly installed secondary drive, I'm still frustrated. It shows up, but doesn't register as actual space... I may go back through this thread and try to undo what we've done, then try to get it working with the Gparted CD I made...

Here's a thought... I guess I've been assuming that Linux works just like windows with regards to hardware installs... I have the primary set as the master and the secondary set as slave. That's not causing any problems, is it? Would it work differently if they were both set to cable select?

n.

---

### Post by Jose Catre-Vandis on 2007-10-31
You will have more success using the Live Cd version of Gparted as you can work with all your partitions.

Leave swap where ubuntu puts it, no need to move it anywhere else.

Re hardware, if both drives are on the same IDE cable then yes, Master and Slave is fine. However you probably have a CDrom drive onboard too, so set up your first hard drive as master with Cdrom as slave on one cable (IDE-0), and the second hard drive as master on the second cable (IDE-1)

---

### Post by Nathan Otis on 2007-10-31
I'm at a complete loss on the secondary. Ubuntu sees it, mounts it and there's a folder under media. It still reads the same available size as the primary and nothing I move to it changes those numbers.

What now?

---

### Post by Nathan Otis on 2007-11-01
> **Jose Catre-Vandis said:**
> Do the following:

add the line:
```
/dev/hdb1     /media/HDD2    ext3    defaults     0   2  
```

save and reboot.

Just realized this line wasn't in fstab. I'm trying to get it in there, but it won't let me save. Permissions again.

n.

---

### Post by Nathan Otis on 2007-11-01
Victory is mine!

I found instructions on an "Open as root" script. Added that line to fstab and POOF! New HDD2 on my desktop.

I do still need a little help, though. Clean up from the initial attempt. I still have my secondary mounting under Media as a different name (is this clear?) It's mounting correctly as "HDD2", and also as "Secondary".

How do I undo these changes?

Now that I think of it... I'd be perfectly happy if HDD2 didn't mount under /media, but rather showed up only on the desktop. Is that possible?

Thanks with the help so far. This is definitely the home stretch.
n.

---

### Post by Nathan Otis on 2007-11-01
> **Nathan Otis said:**
> 
I do still need a little help, though. Clean up from the initial attempt. I still have my secondary mounting under Media as a different name (is this clear?) It's mounting correctly as "HDD2", and also as "Secondary".

How do I undo these changes?
n.

Victory is STILL mine. I got the erroneous "Secondary" out of /media so all is well.

n.

---

