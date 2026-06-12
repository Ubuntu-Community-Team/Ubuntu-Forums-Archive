---
title: "What are .fr- hidden directories?"
date: 2012-12-25
forum: General Help
---

### Post by ggordon on 2012-12-25
I have three hidden directories in my home directory with names that begin with .fr-  The contents of each of them appears to be unrelated.  One of them contains a huge archive file named "files.tgz" containing what appears to be a backup of my /etc and home directories from several years ago.  The file is 2.5 GB, so I would like to delete it if it is not being used for anything.

The three directories were created on consecutive Thursdays a couple of years ago.  The first file created was the huge archive file.  The next two just contain individual directories and files.  It kind of looks like I might have been trying out a backup application.  However, I have been using backuppc since before these directories were created.  So I don't know why I would be trying out another backup application; especially to backup just /etc and my home directories.

Anybody know how or why these .fr- directories get created?

---

### Post by StinkySQL on 2012-12-25
Sounds like an initial backup and then some incremental backups following-on.  I am unaware of a backup program by default running - I don't have them with 12.04 for example.

SS

---

### Post by Kirk Schnable on 2012-12-25
Just to throw some unconfirmed speculation on the table... File Roller is the program used as an archive manager by default. Maybe these were temporary files used by File Roller at some point, but were never deleted?

Unconfirmed, as I have not verified where File Roller puts it's temporary stuff... Just a thought.

---

### Post by MG&amp;TL on 2012-12-25
> **Kirk Schnable said:**
> 
Unconfirmed, as I have not verified where File Roller puts it's temporary stuff... Just a thought.

Normally in /tmp. But I guess older versions, bugs, failed saves...

---

### Post by haqking on 2012-12-25
> **Kirk Schnable said:**
> Just to throw some unconfirmed speculation on the table... File Roller is the program used as an archive manager by default. Maybe these were temporary files used by File Roller at some point, but were never deleted?

Unconfirmed, as I have not verified where File Roller puts it's temporary stuff... Just a thought.

it is, it is an old bug [https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/245716](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/245716)

it puts them in home instead of /tmp

---

### Post by Kirk Schnable on 2012-12-25
> **haqking said:**
> it is, it is an old bug [https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/245716](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/245716)

it puts them in home instead of temp

Awesome find!  Looks like my hunch was correct, then.

---

