---
title: "mount points vs &quot;Location&quot; name - can I rename?  hardy 8.04"
date: 2008-04-28
forum: General Help
---

### Post by TokyoYank on 2008-04-28
During full 8.04 installation, I indicated for my 100 GB fat32 partition with home movies to have the mount point /media/Movies, and indeed it mounts there by default when I boot.  But the GNOME desktop icon (which appears by default) and the "Location" is named "100GB" with no option to change it.  Other mounts are similar; for example 2 other ext3 partitions are all indicated by their total size, not more useful names that I can remember.  When I use *nautilus --browser* to go to /mount/Movies, the directory location panel (on the left) highlight changes from /mount to "100GB".  In /etc/fstab I see entries for each partition just as I indicated at installation, but I don't see any indication of a name to use.


* How / where are the GNOME "Location" and desktop icons named?

* Is there any way to change it?


I wonder if /media was a bad place to use a static mount, since GNOME uses it by default for CD-ROMs..  Or maybe I just don't know the way to make GNOME rename it.  In 7.10 I could rename the mount, but I forgot exactly what I did then.  

Thanks

---

### Post by vanadium on 2008-04-28
You might try giving the partition a volume label. I expect, but I am not sure, that the volume will then be automounted named according to the label. Here you find how you can set volume labels: the procedure differs according to the file system

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Indeed I agree with you that static mounts are not at theri best place under /media. I would use the traditional /mnt for static mounts.

---

### Post by TokyoYank on 2008-04-28
> **vanadium said:**
> [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Indeed I agree with you that static mounts are not at theri best place under /media. I would use the traditional /mnt for static mounts.

Thanks a lot!  .. any idea why there was a point and click option in 7.10 that doesn't exist now?  I mean, I don't recall doing anything different between my NTFS, FAT32, and ext3 mounted drives last time.  ... and I tend to think it was GNOME driven.  The "Places" labels had capitals *and* lower case, so..  the help you listed seems different.  I'm not complaining, I'm just curious :) 

About the /media location:  I gave /mnt a try, in case GNOME is acting strange due to a conflict with the mount directory name.  When unmounted the desktop icon / "Places" entry disappeared, but nothing came back when I mounted it successfully under /mnt  ... this makes me think that the desktop icons ***are*** a result of my mounting them in /media  .. anyway, I'll restart GNOME to see if it might also be a behavior at startup.  I'll post again if something changes

---

### Post by vanadium on 2008-04-28
Hardy uses a new system, gvfs, to handle this and that is why some things are different.

Anything mounted under /media will show up as a desktop icon. That is why it is nice to mount permanent volumes under /mnt: you do not need a desktop icon for these.

---

### Post by quixote on 2008-04-28
Vanadium: is there an easy how-to somewhere on making desktop icons for drives?

I realize that to change the mount point for my drives I (presumably??) just edit /etc/fstab.  But how do I make those nice little drive desktop icons?  Just making a link doesn't really do it.  There's no mount/unmount option then, and so on.

Also, my big problem with renaming vfat drives as per the RenameUSBDrives link -- and I know this is nobody's fault but Windows -- is that THEY'RE ALL UPPERCASE.  I HATE UPPERCASE.  I desperately want lowercase names that make sense to *me*.  Am I right in thinking that if the partitions are mounted to /mnt and I learn how to make drive-desktop-icons then I'll be able to do that?

---

### Post by vanadium on 2008-04-29
Drives automatically acquire a desktop icon when they are mounted under /media. There is no way I know to create similar desktop icons for drives mounted elsewhere.

Drive icons are a bit of a Windows thing. In Linux, it is all treated as part of your file system and accessed in a coherent way, whether it is a partition on a drive or a network connection. Working with symbolic links from within your home directory is a lot more convenient: you can have all your data within reach from within your home directory, without a need to navigate out of it.

For removable devices things are a bit different. They are not permanent and for that reason appear conveniently on your desktop for as long as you need them.

I am not sure why you would not be able to give a label in lowercase with mtools.

---

### Post by TokyoYank on 2008-04-29
> **quixote said:**
> I realize that to change the mount point for my drives I (presumably??) just edit /etc/fstab.  But how do I make those nice little drive desktop icons?  Just making a link doesn't really do it.  There's no mount/unmount option then, and so on.

Sometimes I also wish there was an GNOME interface for mounting disks, similar to the ubuntu install step...  but maybe it doesn't exist since it'd be easy for a beginner to hose their systems, or that they should learn the command line.  ... I don't know. 

I agree with vanadium however:  a link on the desktop works fine, and it even goes to the folder I use most often.  And I can select a custom icon if I really want to.

---

### Post by verbage on 2008-04-29
I just want to point out that this issue of giving mounts a name based on their size is apparently a known and active bug.  For more details, see the thread where this was discussed a few days ago at the following URL:

[http://ubuntuforums.org/showthread.php?t=766167]("http://ubuntuforums.org/showthread.php?t=766167")

---

### Post by vanadium on 2008-04-30
I am not sure whether this is a bug or a feature. Naming is only done based on the volume label now, and this might be considered to be a more consistent approach. For yet another thread on this, see [http://ubuntuforums.org/showthread.php?t=773880](http://ubuntuforums.org/showthread.php?t=773880)

---

### Post by verbage on 2008-04-30
> **vanadium said:**
> I am not sure whether this is a bug or a feature.

Well, it appears to be an active bug (or possibly regression)--check out the link I pointed out just two comments above to confirm this.

Why is this a bug and not a feature?  Because, Ubuntu has explicitly specified/proscribed what the behavior should be in their wiki, and what happens does not follow that specified/proscribed behavior.  The specified/proscribed behavior for naming these mounts on the desktop should be:

--use the label if there is one available (also for unmounted partition) 
--if there is no label, use the hal vendor information 
--if there is no vendor information, append the /dev device name 

Note that the list above is quoted from the Ubuntu wiki at [https://wiki.ubuntu.com/DesktopVolumesRepresentation]("https://wiki.ubuntu.com/DesktopVolumesRepresentation").  Note that this appears to be the behavior demonstrated by GG/7.10 according to my limited use of it.  But this is not the behavior by HH/8.04 in my experience--the last step is not followed, instead, we get the "XX GB" labeling.

As this bug is easily worked around by labeling the drives, I think it is appropriate that it is has a low priority.  That said, I hope it is eventually fixed because I do prefer the specified/proscribed behavior (like GG/7.10 had) vs. what happens in HH/8.04.

---

### Post by quixote on 2008-05-01
vanadium: thanks for the info re /media and /mnt.  I didn't realize that was the convention.  I put those drives under /mnt because I don't, indeed, need them on the desktop.  For some reason, that made everything owned by root, ever though users could mount them as per my fstab options.  ??  I had to add umask=0000 to my fstab options for the partitions involved, and now everything works.  Hopefully, that isn't some sort of massive security hole.  I'm not too familiar with the ins and outs of umask.

I'd like to add to the feature / bug discussion.  It may be more consistent from the OS standpoint, but, believe me, from the user standpoint that isn't just a bug.  It's a centipede.

No matter how the OS wants to refer to it, consistency is BAD from the user's standpoint.  We need to be able to name partitions according to whatever works for us!

---

