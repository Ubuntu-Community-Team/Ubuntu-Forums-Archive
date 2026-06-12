---
title: "GAH! NTFS mounting problems"
date: 2006-07-27
forum: General Help
---

### Post by Lunar_Lamp on 2006-07-27
I was having no problems with mounting my windows ntfs partition as read only.  I then mounted it using ntfs-3g as read/write - with no problems.  I had all my music playable in amarok.  

I booted up into windows to do some things.  After booting into linux, I then connected up a USB HDD which was a 230gb NTFS partition (I say both of these as I hadn't done them in ages, so think they might be causes).  The NTFS partition on my laptop will now not mount properly.

It used to mount on boot, which it doesn't now.  I tried: 

```
ed@PMSEH:~$ mount -a
mount: only root can do that
ed@PMSEH:~$ sudo mount -a
Volume is dirty.
Run chkdsk and try again, or use the force option.
Mount failed.
ed@PMSEH:~$ chkdsk
bash: chkdsk: command not found
ed@PMSEH:~$ sudo chkdsk
sudo: chkdsk: command not found

```

I then tried:
sudo mount /dev/hda1 /media/hda1

This works, but, only gives root access to the files.  What am I doing wrong, and why has is stopped automounting like I wanted it to previously (read and write to all, or at least to my normal user)?

My /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs-3g    silent,umask=0,locale=en_GB.utf8    0    0
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by carontis on 2006-07-27
Let me know 1 thing: do you use that hdd as primary (system) or not? 'cause the last written in fstab should report also the check order. Look at the final "... 0   0" and try to change it to "...0  3" this 'cause I have seen it shoul be the 3rd hdd you mount; after this give necessary permission to all users in read and write. It should work. You should also reboot your pc and watch the listing it shows during boot.

---

### Post by Lunar_Lamp on 2006-07-27
Well I changed the /dev/hda1 as you suggested ("0   0" to "0   3"):

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs-3g    silent,umask=0,locale=en_GB.utf8    0    3
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I have the same problem still.  I'm not sure what you meant by changing permissions - where do you want me to change permissions?  In fstab itself, if so how?

---

### Post by givré on 2006-07-27
> Volume is dirty.
Run chkdsk and try again, or use the force option.
Mount failed.
The chkdsk command it want you to run is the windows command. There is not yet an NTFS chkdsk for linux.
Also be sure that your NTFS partition was unmounted cleanly when you reboot from windows (no suspen/hibernation, no hard boot)
ntfs-3g need an clean partition so it will not corrupt your data.
And never using the force option.
If you mount/unmount things cleanly, you shouldn't have any problem.

---

