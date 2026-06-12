---
title: "unison and fat32"
date: 2006-11-18
forum: General Help
---

### Post by harty83 on 2006-11-18
Hello,

In dapper I used unison fine.  I upgraded to edgy and am now having issues.

I have two fat32 partitions.  One on my laptop and one on my desktop.  Both are mounted as follows via /etc/fstab

```
/dev/hdb1   /media/storage   vfat   defaults,umask=000   0   0
```

Now I can mount via ssh or samba and read/write fine.  But Unison seems to be having issues.

I run unison and it determines changes.  Good so fo.  So I click on go and everything fails to copy.

Here is an example of the error messages I get:

```
test
Error in setting permissions:
Operation not permitted [chmod(/media/storage/Shared_Folder/.#test.6e1a41542005e942c0b17921826f56cd.unison.tmp)]
```

Any clue what is going on?  I can run unison by root and connect to root@mydesktop and it works.  So it def has something to do with permissions.  All directories are fully readable and writeable by everyone so I'm not for sure what the deal is.

Thanks in advance!
Alan

---

### Post by paxmark1 on 2008-03-14
My post elsewhere awhile back - no one seems to answer how to utilize this via u-gtk.  So here is a partial solution for you that uses the command line version of unison

side issue.

I had problems with unison between puter and USB, but got it to work in the text mode via appending

-perms=0


How can I get that set up for the graphical GTK version of unison?

peace

---

### Post by awry on 2008-03-17
Unison stores sync profiles in ~/.unison/*.prf.  Edit the relevant prf file, and add a line 'perms = 0' and it will always ignore permissions for that profile.

See also: [http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html#profiles](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html#profiles)

---

### Post by wieman01 on 2008-03-18
Thanks for that hint. I thought it is a FAT32 specific issue and reformated the drive so that it uses 'ext3' instead. 

Anyway, 'ext3' is less trouble but I guess you don't have a choice when it comes to USB devices.

---

### Post by eudemus on 2008-03-18
It's also true - as I found - that even with perms=0 in the Unison profile, it has copying problems (exactly the situation you describe - no problem reading and writing to the drive as my own user, but *unison* does get problems.).

Apparently this is a bug in Unison - it is fixed in the latest stable version of Unison (2.27), but not in the version in the Ubuntu repositories (2.13, I think). It tries to do things with permissions even when you have told it not to.

I had another work-around for my USB flash drive.
[http://ubuntuforums.org/showthread.php?t=727331](http://ubuntuforums.org/showthread.php?t=727331)

Cheers.

---

