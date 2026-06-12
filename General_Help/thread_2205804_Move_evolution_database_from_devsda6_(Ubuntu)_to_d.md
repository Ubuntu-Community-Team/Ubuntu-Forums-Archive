---
title: "Move evolution database from /dev/sda6 (Ubuntu) to /dev/sda3 (data files)"
date: 2014-02-16
forum: General Help
---

### Post by cigtoxdoc on 2014-02-16
I want to move the database files that go with evolution e-mail (> 5 GB) to a partition with my data files and much more room.  How do I do this?  Documentation for evolution apparently does not cover this (or I missed something).  I have heard of just moving  the /.evolution/ folder and subfolders, but that doesn't seem right.

Thank you,

John

---

### Post by Elfy on 2014-02-16
I do similar with xchat and a couple of other apps. I use symlinks here.

I'd backup the current .evolution files first however you want to - I'd just rename the folder evolution if you back it up to the same place you want to move to.

Then 

```
ln -s /path/to/datapartition/.evolution  /home/user/.evolution
```

---

### Post by cigtoxdoc on 2014-02-16
Thank you for your suggestion.  I setup the sym link: /media/MyChemistry/evolution /home/john/.local/share/evolution.  The terminal output appeared to show the results of the link, but it didn't work (imported new folder into the evolution under /home/john/.local/share/ not the one I wanted.  Here is some terminal output (note the first link shown does work):

john@john-Vostro-3500:~$ realpath /home/john/Documents/mydocuments
/media/MyDocuments
john@john-Vostro-3500:~$ realpath /home/john/.local/share/evolution
/home/john/.local/share/evolution
john@john-Vostro-3500:~$ realpath /media/MyChemistry/evolution
/media/MyChemistry/evolution

Where did I go wrong.  I want to put all datafiles for evolution under /media/MyChemistry/evolution and then delete the datafiles under /home/john/.local/share/evolution

John

---

### Post by cigtoxdoc on 2014-02-16
Apparently, someting else is going on.  After I made another attempt by moving the evolution directory to the other partition, I found the InBox had gotten lost.  I needed to restore evolution from the backup I made ealier today.  The restore put everything back in my home directory.

John

---

### Post by faial on 2014-02-17
In relation to the discussion in this thread.

My Evolution folders are beginning to feel a bit heavy so I want to backup Evolution but do not wish to use the File -> Back Up Evolution Data feature because it creates one giant file and only allows for complete restore. I want to restore folder by folder as needed  (e.g. Inbox, Sent, etc.). What exactly do I have copy/backup and what shall I do when restoring of a particular file is needed?

Thanks for any help.

---

