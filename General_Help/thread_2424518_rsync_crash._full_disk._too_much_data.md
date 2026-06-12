---
title: "rsync crash. full disk. too much data"
date: 2019-08-10
forum: General Help
---

### Post by Kevin McCready on 2019-08-10
Is there a way for rsync to tell me that the data I am trying to copy from one place to another won't fit. rsync just crashes.

I think my hard disk is now full of crap. How can I delete it all.

---

### Post by SeijiSensei on 2019-08-10
Unless you've been using sudo a lot, most anything you created is in your home directory. I'd start by looking there.

Another possibility is that /var/log has grown excessively large.  This can be especially true if your machine/installation has issues and throws a lot of errors which are being logged in /var/log/syslog or maybe /var/log/kern.log. You can only edit the contents of this directory as the root user by using sudo.  You'll also see a bunch of backed-up copies of the log files compressed with gzip (.gz files). You can probably delete the older ones without losing much.

If you do see some really large files in /var/log, you need to examine them carefully to see whether there is a problem on your system that needs fixing.

There is also the "find" command which can scan your drive and identify files larger than a certain size.  It has a pretty complicated syntax, though, so I'd start first by looking in your home directory and /var/log/.

If you run rsync with the -n switch, it will perform a "dry run."  I don't recall whether that will flag a problem with running out of space.  I back everything up to a [4 TB external USB drive]("https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817?Item=N82E16822178817"), so I don't see errors like that.

---

### Post by TheFu on 2019-08-10
An error - "out of disk space" - will be displayed.  You seem to be notified.

To delete files, use the **rm** command. I suspect that really isn't the question you wanted to ask. You can also use 'find' to delete files, but almost always, this is a good way to completely wipe an OS.  I've done it, accidentally.
 
rsync doesn't remove files, unless you explicitly ask it to do that.  The manpage has information on a multitude of options to control how files are remove in the target directory based on the file(s) not existing in the source area.

If you need to find the large files on your system which might free up storage with little effort, 
```
find $HOME  -type f -size +3G -exec ls -lh {} \;
```
will help find any files over 3GB in size.  Really, any files over 500M are probably worth looking at.
To delete the found files, just change the -exec .... stuff into -delete.
Be very careful.  The files will be gone.  If you need them back, then a backup is the only way.

---

### Post by Kevin McCready on 2019-08-10
Thanks for the help. Appreciate it.

---

