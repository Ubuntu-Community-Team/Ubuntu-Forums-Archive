---
title: "Exlusions file for backup operations using rsync"
date: 2014-11-26
forum: General Help
---

### Post by agharbeia on 2014-11-26
The following is the content of an exclusions file I use with rsync when I perform full /home backups. It simply leaves out various types and locations where the files are redundant. Examples are browsers' cache directoris, trash, automatically-generated thumbnails, and backup filetypes, as well as anchorage directories of cloud storage. The rationale is to speed the backup process up, and reduce the size of datathat needs to be transferred and/or stored, specially when it's an emergency backup operation.

I pass that file as a parameter to --exclud-from= option along with othe rparameters:

Do you have the same concern? Ddo you  use this or a similar method? What else does your exclusions file contain?
```

*.*~
*.bak
.bitcoin/blocks
.bitcoin/*/*.sst
cache
Cache
.cache
*.cache
.config/smplayer/file_settings
.config/ubuntu-tweak/appcenter
.config/ubuntu-tweak/sourcecenter
Dropbox
.jdownloader/jd
.jdownloader/libs
.jdownloader/licenses
.jdownloader/plugins
.local/share/Trash
.~lock.*
*.log
.macromedia/Flash_Player
.mozilla/firefox/Crash Reports
.SpiderOak
Temp
.thumbnails
thumbs
tmp
UbuntuOne
ubuntuone


```

---

### Post by kevdog on 2014-11-26
List looks good to me.  It just depends on the situation.  Sometimes depending on bandwidth I don't want to back up big .iso or .mpg files.  It would just depend on your situation.

---

### Post by sudodus on 2014-11-26
> **kevdog said:**
> List looks good to me.  It just depends on the situation.  Sometimes depending on bandwidth I don't want to back up big .iso or .mpg files.  It would just depend on your situation.

+1 :-)

---

### Post by rbmorse on 2014-11-26
I use "BackInTime", which is a GUI front-end for rsync that makes management of the backup store a bit easier.  BackInTime's recommended exclusion list includes:
```

.gvfs, 
.cache*
[Cc]ache*
.thumbnails*
[Tt]rash*
*.backup*
*~
 /root/Ubuntu One 
.dropbox*
/proc/*
/sys/*
/dev/*
/run/*

```

Not had any problems.  

As an aside...would someone explain, in the context of an rsync exclusion list, the difference between: 

/sys 
/sys/ 
/sys/*

---

### Post by sudodus on 2014-11-26
See ```
man rsync
```

```
       Perhaps the best way to explain the syntax is with some examples:

              rsync -t *.c foo:src/

       This would transfer all files matching the pattern *.c from the current directory to the direc&#8208;
       tory  src  on  the machine foo. If any of the files already exist on the remote system then the
       rsync remote-update protocol is used to update the file by sending only  the  differences.  See
       the tech report for details.

              rsync -avz foo:src/bar /data/tmp

       This  would  recursively  transfer all files from the directory src/bar on the machine foo into
       the /data/tmp/bar directory on the local machine. The files are transferred in "archive"  mode,
       which  ensures that symbolic links, devices, attributes, permissions, ownerships, etc. are pre&#8208;
       served in the transfer.  Additionally, compression will be used to reduce the size of data por&#8208;
       tions of the transfer.

              rsync -avz foo:src/bar/ /data/tmp

       A  trailing slash on the source changes this behavior to avoid creating an additional directory
       level at the destination.  You can think of a trailing / on a source as meaning "copy the  con&#8208;
       tents  of  this  directory"  as  opposed to "copy the directory by name", but in both cases the
       attributes of the containing directory are transferred to the containing directory on the  des&#8208;
       tination.   In  other  words,  each of the following commands copies the files in the same way,
       including their setting of the attributes of /dest/foo:

              rsync -av /src/foo /dest
              rsync -av /src/foo/ /dest/foo


```

I think **dir/** will select all files (including hidden files and hidden directories) while **dir/*** will not. I'm not sure if this makes a difference in case of exclusion, but it does make a difference for copying.

*Edit:* I suggest that you test what happens when you perform a 'DRY RUN' with verbosity (with the options **vn**)

---

### Post by ajgreeny on 2014-11-26
Your way of doing this is exactly the same as I use with both rsync and grsync when I backup my /home, though as I have a different assortment of applications to you, my list is, not surprisingly, different as well.

I don't bother to back up anything from the root partition as it is so quick to reinstall if it came to it; it is all my /home files and folders that are so important to me and can not be replaced if I have no backup of /home.

---

### Post by agharbeia on 2014-11-26
You're absolutely right.
I also do that on-the-run in some cases. I just didn't want to include it in case some of these files for some people are irreplaceable.
In fact my original list excludes virtual machine disks as well, since I have some of those too.
I'm also recently using a NAS for storage of videos and images, so their backup rutine is different from that of /home

---

### Post by agharbeia on 2014-11-26
> **kevdog said:**
> List looks good to me.  It just depends on the situation.  Sometimes depending on bandwidth I don't want to back up big .iso or .mpg files.  It would just depend on your situation.

You're absolutely right.
I also do that on-the-run in some cases. I just didn't want to include it in case some of these files for some people are irreplaceable.
In fact my original list excludes virtual machine disks as well, since I have some of those too.
I'm also recently using a NAS for storage of videos and images, so their backup rutine is different from that of /home

and...
rbmorse,
I think in your case you're starting your backup routine at the root of the systm. This is another differenc.

---

