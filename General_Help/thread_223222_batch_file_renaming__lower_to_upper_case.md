---
title: "batch file renaming / lower to upper case"
date: 2006-07-26
forum: General Help
---

### Post by SpectralDesign on 2006-07-26
I've searched around and seen ways to rename groups of files, but they all seem to be for extensions only, i.e. change *.htm to *.html

In my case, I want to change the case on some files.... background: I used to store my camera's pics on a FAT32 volume, now I store them on EXT... well, the old files all have lower-case, and as I copy new photos to the new partition they maintain their uppercase names the camera gives them.

This leads to odd sorting behaviour, as regardless of the picture number, the preceeding DSCN (or dscn) splits the file sort.  So, I'd like to do a bulk (batch) rename of all the pics that came over from the FAT32 to make dscn001.jpg, dscn002.jpg, etc. into DSCN001.jpg, DSCN002.jpg, etc...

I know there must be a way (perhaps with SED) to get this done, but I've never been able to get my head wrapped around regular expressions enough to figure out how to do this operation....

If there were a way to do this batch rename recursively it'd also save some extra work!

Thanks for any pointers!

^Curtis

---

### Post by croak77 on 2006-07-26
Try from a terminal use the rename command:

rename 'y/a-z/A-Z/' *

That will rename all files and folders too in a directory to all upercase.

To rename recursively you can use find with rename;

 find ./ -type f -exec rename 'y/a-z/A-Z/' {} \;

That will find all files (-type f) in current and sub directories and rename to all uppercase.

---

### Post by roberTO on 2006-07-26
Or install thunar and plugins from repo!!!
Great batch renamer tool!!!

---

### Post by SpectralDesign on 2006-07-26
Croak77,

Thanks!  I used the recursive version, it had a couple hiccups: it was trying to rename files inside folders that had either (or both) white-space ot lower-case, but I just renamed the few folders to replace white spaces with underscores, and changed them to upper-case, and viola', the pics are all renamed and sort apropriately now!

Thanks again.

roberTO,

I'll have to check out the tool(s) you mention, thanks!

---

