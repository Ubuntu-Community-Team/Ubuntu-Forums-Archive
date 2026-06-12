---
title: "Mount ntfs internal hard drive with read and write"
date: 2008-04-30
forum: General Help
---

### Post by hurdevan on 2008-04-30
I'm running Ubuntu 7.04 and have a second 120 GB internal hard drive that the system refuses to mount has read and write. I can't update my system because it will go wacky. 
I have downloaded and installed ntfs-3g.

The string that ntfs-3g put in the /ect/fstab file gives me an error when trying to mount.

Running ntfsfix says that it will not fix it.

I did something to /ect/fstab file that wont let me unmount the drive(I probably need to restart the system)

The drive I'm trying to mount is /dev/hda1.

I have looked at a couple of thread about this but non helped.

How in the world do you mount /dev/hda1 with read and write properties??????

---

### Post by TeoBigusGeekus on 2008-04-30
Install ntfs-config from synaptic, then go to applications->system tools->ntfs configuration tool(or something like that-I'm on a xp machine now).
Select your volume and check all the boxes.
I hope that helped you...

---

### Post by hurdevan on 2008-04-30
I already have it it gives me the fallowing error
---------------------------------------------------------
Mounting /media/ntfs failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
-------------------------------------------------------------------

---

### Post by TeoBigusGeekus on 2008-04-30
If you are dual-booting with window$, you need to boot up windows, shut down properly and then boot up Ubuntu...

---

### Post by hurdevan on 2008-04-30
I'm not duel booting windows.

---

### Post by TeoBigusGeekus on 2008-04-30
Have you tried fsck?

---

### Post by hurdevan on 2008-04-30
Not but i just did.. it did not do anything but tell me this

---------------------------------------------
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: clean, 98166/9453568 files, 845196/18880383 blocks

---------------------------------------------

---

### Post by TeoBigusGeekus on 2008-04-30
Ok, boot up with the live cd and then run fsck...

---

### Post by hurdevan on 2008-04-30
I will just back up everything on to my first hard drive and then formate it to fat. I was going to do it anyways.

Thanks

---

### Post by TeoBigusGeekus on 2008-04-30
Sorry if I wasn't of any help...

---

### Post by hurdevan on 2008-04-30
you were help but I reslised that what i was doing was pointless.
But know I want to know how to mount ext3 hard drive

---

