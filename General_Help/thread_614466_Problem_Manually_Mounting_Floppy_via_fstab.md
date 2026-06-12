---
title: "Problem Manually Mounting Floppy via fstab"
date: 2007-11-16
forum: General Help
---

### Post by blackhole54 on 2007-11-16
Hi All,

I am using a headless computer running *edgy eft*.  Even though *gdm* is running, it is not set up to autologin anybody, so there isn't anybody logged into the GUI.

Here is my */etc/fstab* file:

```

# /etc/fstab: static file system information.
#
# file system&amp;amp        mount point&amp;amp      type           options          dump         pass
proc	/proc	proc	defaults	0	0


/dev/sda1	/	ext3	defaults,errors=remount-ro	0	1
/dev/sda7	/var	ext3	defaults,errors=remount-ro	0	2
/dev/sda6	/mnt/sda6	ext3	defaults,errors=remount-ro	0	 2
/dev/sda9	/mnt/sda9	ext3	defaults,errors=remount-ro	0	 2
/dev/sda2	none		swap	sw			0	0
/dev/sdb	/mnt/usb	auto	user,noatime,umask=007	0	0
/dev/sdb1	/mnt/usb	auto	user,noatime,umask=007	0	0
/dev/fd0	/mnt/floppy	auto	user			0	0

```

If I place a floppy with a FAT filesystem on it in the drive, and via SSH (as a regular use) type:

```

user@ratel:~$ **mount /dev/fd0**
mount: I could not determine the filesystem type, and none was specified

```

Giving the command as *root* gives a slightly different message, but is equally unsuccessful.  Things work fine if I type

**sudo mount -t vfat /dev/fd0 /mnt/floppy**

An old RH7.0 installation has no trouble determining the filesystem type on  this disk,  with the command:

**mount /dev/fd0**

Also, if (by analogy) I put plug in a USB key drive with a FAT filesystem and type

**mount /dev/hdb1**    or    **mount /dev/hdb**

as appropriate for the device, things work fine.

I have tried creating an */etc/filesystems* file with the line *vfat* in it to no avail.  Does anybody have an idea what could be wrong?

---

### Post by mdpalow on 2007-11-16
Might this work in your fstab?

/dev/fd0  	/media/floppy  	auto  	rw,noauto,user,sync  	0 0

---

### Post by blackhole54 on 2007-11-16
Thanks for the response, mdpalow.

I changed *fstab* as you indicated and created the directory */media/floppy*.  I still get the same results.

---

### Post by mdpalow on 2007-11-16
I guess since the -t works you could try this in your fstab:

/dev/fd0 /media/floppy vfat rw,user,sync 0 0

leaving out the noauto, I suppose you wouldn't have to even mount it; as it already should be.

---

### Post by blackhole54 on 2007-11-16
> **mdpalow said:**
> I guess you could try: ...  leaving out the noauto, I suppose you wouldn't have to even mount it; as it already should be.

Not really, since the floppy won't normally be present at boot.  But your post did _finally_ get me to focus on *noauto*, which, as posted, I'd left off of the USB entries as well.  So I got *noauto* on all of the lines where it belongs, rebooted for good measure, and tried again.  Same result.  :(

I tried a new floppy as it comes out of the box, with the same result.  But once again, the RH7.0 system autodetected the filesystem fine.  I then formatted the new floppy (on the Ubuntu system) with **mkdosfs**.  After doing that, both the Ubuntu system and the RH system autodetect it.  :confused:  Of course, since I generally will use floppies on multiple systems, including MS systems, and since I have preexisting floppies that I occasionally will want to read, formatting the floppy on the Ubuntu system is not a general solution.

For now, I have changed my *fstab* file to specify *vfat* instead of *auto* detect, and that seems to work fine with all the vfat floppies.  And since it is seldom, if ever, I will want to use a non-vfat floppy, I gues I will just live with that, unless I or somebody else comes up with a brilliant solution.  But it is frustrating that unless Ubuntu formatted the floppy, it can't autodetect the FS.

Thanks for your help.  If the solution to this mystery occurs to you, please do post it.

---

