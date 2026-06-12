---
title: "gvfs-fuse filled up root / ... help!"
date: 2008-05-07
forum: General Help
---

### Post by quixote on 2008-05-07
I filed a bug report on this ([bugs.launchpad.net/ubuntu/+source/gvfs/+bug/227753](bugs.launchpad.net/ubuntu/+source/gvfs/+bug/227753)), but I also need a fix!  Hope somebody can help.  The workaround listed under "gvfs and disk usage" ([ubuntuforums.org/showthread.php?t=748778](ubuntuforums.org/showthread.php?t=748778)) doesn't work for me.  The bug report mentioned ([bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789](bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789)) is also not the same issue.  At least, it certainly isn't fixed like the report optimistically says!

This is a major problem since it prevents any operation that wants to store to the filesystem, including /tmp.  gvfs seems to have decided that one of my network drives is in my root partition.  That makes it think the root partition is full.  (it isn't, really.) 

The problem is this:

A backup, made with Simple Backup, is in /mnt/mediavault/backup/computer-backup-filename.ful .  That dir and backup now show up no matter what.  I can't umount the partition, even using -f.  I moved the backup out of that dir, and it still lists as being in that location, although it no longer is.  In desperation, I tried to remove ~/.gvfs, hoping that would straighten gvfs out, but it won't let me since the resource is busy.

I'm running, 8.04.  gvfs-fuse 0.2.3-0ubuntu5

This is similar to, but not the same as these bugs:  [https://bugs.launchpad.net/ubuntu/+bug/217389](https://bugs.launchpad.net/ubuntu/+bug/217389) "root partition usage reaches 100% without reason."  In that case extra backup files weren't noticed and could be removed once they were.

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789) "disk usage analyzer shows twice disk capacity"  Deselecting gvfs-fuse-daemon and rebooting did not solve the problem for me.  Also, this bug is said to be "fixed upstream" but whatever is causing my problem is not fixed :(  

How can I wake gvfs up to the fact that 2.2GB are NOT on my root partition, but somewhere else entirely?!  My computer is near-useless and I'm desperate for a workaround.  Help!!

---

### Post by t-molli on 2008-05-16
I need a fix too. Same thing is happening to me. I added my comments to launchpad; not sure if it was yours.

---

### Post by quixote on 2008-05-16
t-molli: my first link to the bug report has the details on what I had to do to get my space back.  Still nothing from anyone who knows anything about this.  I'm not used to this from the previously-stellar Ubuntu crew!  Maybe the poor Heron is molting and they have enough problems on their hands??

Briefly, what I had to do was delete, as root, the backup and the directory on the network drive.  Then I unmounted gvfs-fuse-daemon, and deleted .gvfs directory in both my home and root's, and then I rebooted.

---

