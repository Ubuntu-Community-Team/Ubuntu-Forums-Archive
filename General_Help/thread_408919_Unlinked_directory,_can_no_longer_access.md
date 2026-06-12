---
title: "Unlinked directory, can no longer access"
date: 2007-04-13
forum: General Help
---

### Post by ChrisFontenot13 on 2007-04-13
So I'm looking at what used to be a directory full of about several gigs of PDF's, and all I see is a file with a creation date of October 1973.  
Here's what "ls -Flag" gives me, basically, replacing my username with "user":

?rwxr-xr-x  3 user 4096 1973-03-18 12:15 Texts
drwxrwxrwx  3 user 4096 2007-03-17 18:01 Music

A simple "ls" still shows it in the colors of a directory, but neither "cd" from a terminal nor Nautilus will get me into it.   Nautilus just shows a file.  I think the data is still there but I can't get to it.

I just switched from XP, but I'm at least familiar with *nix systems going back a few years, and I am at a loss; I can recover from the file loss but I'd rather know how to fix something like this than not.

I got a whole bucket full of thanks for anyone willing to help a semi-noob.

Thanks,
Chris

---

### Post by iXneonXi on 2007-04-13
Have you tried accessing the files from outside the distribution you're using, as in trying to see them with a LiveCD or from XP using ext2 for Windows?
If you can see them using the other distros, you might have something mounted to that location oddly enough. Can't say that will help, if other systems don't show the files, try using root and doing "ls -a" and if nothing comes up, you might need to try recovery software.
I'm not a master though, so don't take my word as the only solution.

---

### Post by ChrisFontenot13 on 2007-04-13
I have XP & Ubuntu dual booting with Ubuntu as priority; ntfs-3g mounting my XP partition under Ubuntu and Ext2IFS mounting my Linux partitions under XP.  I can't get into the folder from XP, it says the folder is corrupted & unreadable, the rest of the drive shows up fine. 

fsck -N gives me ... 

fsck 1.39 (29-May-2006)
[/sbin/fsck.ext2 (1) -- /mnt/56Gig/Texts] fsck.ext2 /mnt/56Gig/Texts 

I'm running fsck to try and fix it now, having had a major DUH moment (actually a major DUH weekday) in figuring out how to run a File System ChecK.  "Texts" is now showing up light green text, no bkground on a -Flag, still getting that ? instead of d at the beginning of the permissions, tho.

---

