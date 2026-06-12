---
title: "Keeping track of changes to files in /etc"
date: 2015-11-18
forum: General Help
---

### Post by vasa1 on 2015-11-18
I've modified a couple of files in /etc. They are */etc/logrotate.d/apt* and */etc/logrotate.d/dpkg*. My fear is that some day, some update may over-write these files and I'd then lose the modifications I've made.

To keep track, I've copied over the modified files to my Dropbox folder and have added the following code to my apt-get update/dist-upgrade alias:```
sudo apt-get update && sudo apt-get dist-upgrade && diff -sq /home/vasa1/Dropbox/etc-files/apt /etc/logrotate.d/apt && diff -sq /home/vasa1/Dropbox/etc-files/dpkg /etc/logrotate.d/dpkg
```After *apt-get* does its job, *diff* prints out whether those two files have changed or not:```
Files /home/vasa1/Dropbox/etc-files/apt and /etc/logrotate.d/apt are identical
Files /home/vasa1/Dropbox/etc-files/dpkg and /etc/logrotate.d/dpkg are identical
```

I only use *apt-get update && apt-get dist-upgrade* and so I should catch any changes immediately. But is there a smarter way of monitoring *any* folder (or files) for changes resulting from software upgrades?

---

### Post by TheFu on 2015-11-18
There are many ways.
* versioned backups - which should be done anyway. **rdiff-backup**
* **git** or some other VCS.  
* **etckeeper** - you aren't the first with this idea. [https://help.ubuntu.com/lts/serverguide/etckeeper.html](https://help.ubuntu.com/lts/serverguide/etckeeper.html)

Developers tend to use git. It is a tool they know.

Professional system admins tend to use versioned backups. They know the 1000 other uses of good versioned backups. This is what I use-30-120 days of backups.  /etc and /home are the most important parts of a backup set for desktops.

Hobbyists tend to use etckeeper. My brother in law does.

Files that change will have the mtime altered.
```
find / -type f -mtime -1
```

---

### Post by mcparty2 on 2015-11-18
Two options i'd consider...

rdiff-backups - This performs incremental backups. it's particularly useful, you can run it in cron

rancid - If you want to keep track of the changes to a config file.

---

### Post by tgalati4 on 2015-11-18
Most updates have a post-installation script that will check for such changes and provide you with a choice:

1.  Keep existing configuration file.
2.  Apply maintainer's configuration file--replacing your changes, but making a backup copy in /etc.
3.  Show the differences--allows interactive selection of the configuration file.

Of course, this doesn't help if you have automatic updates enabled.  Answering "Yes" using the -y switch will generally keep the existing config file, but may break a service if there have been drastic changes to the configuration file--which is quite rare.

So, I rely on on time-version backups and the post-installation check for each package.  In other words, I don't worry about it.  I do make copies and take good notes about configuration changes, but the solution depends on how many servers you need to manage.

---

