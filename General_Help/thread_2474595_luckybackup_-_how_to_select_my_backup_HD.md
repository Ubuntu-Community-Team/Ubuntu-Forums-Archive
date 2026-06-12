---
title: "luckybackup - how to select my backup HD ?"
date: 2022-05-03
forum: General Help
---

### Post by jmichaels29 on 2022-05-03
using the app luckybackup - how to select my backup HD ?

I can't figure out how to select my backup HD as the destination

perhaps there is a line I can type in to the field since I can't locate it

?

attached screenshot

---

### Post by TheFu on 2022-05-04
I don't use luckybackup, but nobody has answered in a day ... 

[http://luckybackup.sourceforge.net/manual.html](http://luckybackup.sourceforge.net/manual.html) says to setup a {name}.profile. I have to think the sources and target locations would be contained inside the {name}.profile file.

Backups need to be versioned and automatic, at a minimum.  If a tool doesn't make those things relatively easy, perhaps a different tool should be used?  There are lots of choices.

---

### Post by jmichaels29 on 2022-05-04
Yes, perhaps I'll try something different.  
I used to use "Backups" that comes with Ubuntu, but I simply do not like the billion "duplicity" files that backups creates on the destination HD (it didn't do that when I used it under 20.x lts).
I just need something simple, that when manually told to do so, it just backs up my home folder to the destination HD.  Any suggestions?

Regards,

jmichaels

---

### Post by TheFu on 2022-05-04
Well, if you were using DejaDup or any duplicity-based tool, part of that tools greatness is that it chunks the encrypted backup files into small bits for remote uploading somewhere. The encryption it uses is excellent and if something fails to upload, only the small chunks of files that didn't make it need to be resent. It really is quite brilliant ... but it means that getting 1 file back easily requires using one of the duplicity-based tools. The backups aren't really in any funky format, so it is possible to manually put them back together, if you like, but I wouldn't.

A simple copy just isn't sufficient as a backup.  If that is all you want, use rsync, but as a backup, it can lose the most important aspects on a multiuser system like Linux.  The nice thing is that to restore 1 file or a directory, we can just copy that file/directory back. It is nice, but highly likely that file metadata will be lost.  This is the failure of all rsync and rsync+hardlink versioned backups.

There are tools which do versioning automatically, use nearly the same command that rsync uses, capture file metadata and to restore 1 file, just a copy of the most recent version is needed. In fact, the most recent backup set looks just like an rsync mirror, only older versions are stored as reverse-diffs from the current version.  That tool is called rdiff-backup.  I've posted an example script in these forums for just saving a HOME directory for 1 userid.

I think just copying a HOME directory isn't sufficient and leaves setting up a fresh system in a way that can take days, rather than 15 minutes, but whatever.  By backing up just 2 other things, it is possible to have nearly all system settings (/etc/) and if you create a list of manually installed packages (apt-mark showmanual), then at restore time, that list of manually installed packages can be fed into APT to reinstall all the prior programs that were on the system.  The list of packages is tiny.  /etc/ is tiny.  I have a hard time understanding why people resist including those 2 things in their backups.  They can make restores so much faster and more complete for less than 5 seconds of backup runtime.

But whatever. Do what you think you need.  I used to use a mirror of file, until I was burned and discovered that wasn't nearly sufficient.  90 days of daily, versioned, backups uses about 15-20% more storage than the files alone.  Seems like a bargain to me.  Plus rdiff-backup runs in just a few minutes for each version, after the initial backup is made.  That initial backup takes as long as an rsync or a cp, but after that, the updated versions are just 1-3 minutes. It isn't a big deal.  I've posted and posted and posted, about rdiff-backup in these forums after decades of look at other backup tools.

Consider yourself led to the water. You just need to choose to drink from it. ;)

---

