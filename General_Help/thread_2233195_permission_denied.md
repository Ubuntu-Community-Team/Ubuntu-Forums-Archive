---
title: "permission denied"
date: 2014-07-07
forum: General Help
---

### Post by DrScum on 2014-07-07
I want to synchronize a folder with a backup folder on a network drive using grsync. I mount the folder to be synchronized to the network drive and try to synchronize it with the backup folder located on the same drive. Most of the content is copied but there are some files which cannot be opened on the mounted drive, the error message being permission denied.

I did go back to the original folder and set ownership and permissions but the error persists. I also tried running grsync as superuser without solving the problem. Apparently the permissions set are still not the way they should be.

Thus my question: how to I set the permissions to read and write of a folder including all its content (files AND subfolders plus files and subfolders in subfolders)?

---

### Post by Bucky Ball on 2014-07-07
Do you know which particular files/folders are failing with a permissions error?

Easiest to open the file manager as root and then you have permissions for everything and can copy what you want where you want, but this is not ideal. As you are root there is the potential to severely break your system if you do something wrong. I'll presume you're using Ubuntu, thus Nautilus file manager. So:

```
gksudo nautilus
```

That will open the file manager as root. Be careful. Best to try and find which files/folders it is refusing first, though. You may not want them copied.

---

### Post by DrScum on 2014-07-07
I know about the option of running nautilus as root. However, if you set the permissions of a folder correctly and click on "apply permissions to enclosed files" that option apparently does exactly what it says, it applies the permissions to enclosed files but not to subfolders and files in subfolders. 

It would be very tidious to go through every subfolder included. What I need is an option to set permissions on a folder and have it applied down to the last file in the last subfolder. Which I know might be risky to some extent but how else would I be able to synchronize my laptop with a backup server?

---

### Post by Bucky Ball on 2014-07-07
I use Luckybackup myself (a front end for rsync) and does the job nicely. In the repos. It has many options, one of which is to ignore system files/folders and hidden files/folders.

You don't want lost&found, Desktop, or possibly hidden files/folders backed up, to name a few ...

---

### Post by DrScum on 2014-07-07
I'll give it a try. However, in some cases I want hidden files backed up, e.g. .thunderbird and .mozilla which contain e-mails and browser history and shortcut respectively. I definitely do want those. I also want templates from libreoffice applications which are located in .config.

---

### Post by Bucky Ball on 2014-07-07
Once you get your head around Luckybackup it is fairly straightforward and easy. Took a bit of experimenting, though. You can do a dry run and other checks to make sure things are the way you want before you go for the real thing.

You can also mark files for inclusion/exclusion. Pretty flexible. ;)

Unison is also popular. Also in the repos. Have used that, too, and fine, but just prefer Luckybackup.

---

### Post by DrScum on 2014-07-15
Here are the latest results regarding the problem mentioned in my first post:
I mount a network folder located on a network drive to my laptop and synchronize the folder I want to backup (incremental backup).
using grsync as well as luckybackup (I guess they both utilize rsync) files and folders created on the network drive during synchronization are set to user:nobody and group:nobody. That fact causes the "permission denied" problem during the next run. If I go ahead and set owner and permissions on the network drive manually (using chown -R and chmod -R) the error does not occur but any file/folder copied is again set to owner:nobody and group:nobody. Thus in the following backup run the error would be back unless I reset owner and group manually. 

In grsync I have the option "preserve owner", "preserve group" and "preserver permissions" unchecked.
How can I resolve this?

---

