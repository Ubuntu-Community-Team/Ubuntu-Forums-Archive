---
title: "Periodic Copying/Permissions to network?"
date: 2007-12-04
forum: General Help
---

### Post by Isaacariah on 2007-12-04
Hi there

I am an ICT Technician at a local High School, and as such I am responsible for the booking of computer rooms to staff.

My booking system is simple, a bunch of MS Excel documents saved into folders named after the month.

What I want to do, is have some sort of script etc, that every 10 minutes, will copy my entire booking system folder onto a network folder, and apply read-only permissions to it.

Basically my booking system is held on my windows partition in /media/sda2/Documents and Settings/administrator.DHSERVED1/My Documents/bsys/excel and I want to copy the contents of this folder to smb://172.20.56.10/E$/Central Sharing Area/TeacherArea/COMPUTER ROOM BOOKING then I want it to make the smb folder read-only. The folder on the network also needs the administrator username and password to access it.

Can this be done and set to happen every ten minutes?

---

### Post by stump138 on 2007-12-04
you can try this page here for a timed type script:

[http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/1ec473b3c7eb276cca256e1900258747?OpenDocument]("http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/1ec473b3c7eb276cca256e1900258747?OpenDocument")

Just set to some kind of recursive loop.

That said, I ran into the same issue with something very similar, and tbh, the best thing you can do is put this up on an internal webserver with PHP/mysql or some other type script.  It would seriously reduce the amount of work on your end.  Then you only have to worry about backing up a database once daily.

---

### Post by Prospero2006 on 2007-12-04
I'm a middle school technology teacher with a Ubuntu lab in San Antonio, Texas.
As such, I get no support from the district in terms of software, backups, or the like.
Thus, I have to do it all myself, and yes I have something very similar set up to deal with student folders on a shared network drive. 

Mine works like this:

The students have rwx access to the primary drive, which is backed up to a read-only 
folder every 15 minutes that only I have access to for restoring backups. 

Here are some options. If you can't use all of it, some of this may be helpful.

Step one: set up a Ubuntu box on the network with samba sharing enabled. Better yet, enable the apache web server and email your staff a link to bookmark that has all of the current files ready for download and evaluation.

(Samba can be easily configured so that different users have different access permissions on specific folders, but in your case it might work to serve the information up on a Ubuntu box running apache with a static ip address.)

Step 2: Back up data

First, get the folder with the data mounted on the Ubuntu box so that it can be accessed
from the command line. 
```

cd reservationdirectory/

```
This folder should contain your primary excel files that you edit.
It's easy to map windows resources to a Ubuntu box.
Where is this directory stored exactly on your network?

Let's assume the following:

admindirectory/ = a directory that contains a mapped network resource with 
excel spreadsheets that administrators can read and write to.

reservationdirectory/ = a directory that is shared out to the rest of the school via samba or apache. This contains read only information that is updated every 15 minutes.

Ok, once you have these two locations set up, you run rsync to keep the two in sync every 15 minutes. Save something like this to a text file with global execute permissions. 
```

rsync -a -r --delete /admindirectory /reservationdirectory

```
Then you add an entry to cron, I suggest you download kcron as a front-end manager, 
to execute this script every 15 minutes from now until eternity. 
(If omit the --delete flag, it will never delete anything from the target directory, which is ideal for backups.)

I hope that info helps. Now I'm going to shamelessly plug my classroom podcast:

[http://www.neisd.net/imak/Beck/podcasts/Beck/113007final.mp3](http://www.neisd.net/imak/Beck/podcasts/Beck/113007final.mp3)

Let me know if I can help further. I have a lot of experience working in a school environment with Ubuntu.

---

