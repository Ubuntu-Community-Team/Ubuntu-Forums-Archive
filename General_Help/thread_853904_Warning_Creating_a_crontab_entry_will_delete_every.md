---
title: "Warning: Creating a crontab entry will delete everything in your home folder!"
date: 2008-07-09
forum: General Help
---

### Post by vdawg on 2008-07-09
EDIT: I am an idiot, can someone please delete this?

Atleast that's what happened to me just right now.

Fortunately, I keep all my data on a separate partition so I didn't lose much, except for some documents and scripts but the ironic part is that I wanted to setup a backup script so I created one and threw it into my cron entry, when the following happened : 

```

vic@puter:~$ crontab -e
no crontab for vic - using an empty one
crontab: installing new crontab
vic@puter:~$ ls
vic@puter:~$ ls
vic@puter:~$ pwd
/home/vic

```

Also, all the hidden files and folders (where all the settings are), were left intact,

grrr.

---

### Post by sdennie on 2008-07-09
Creating a crontab with crontab -e will not cause this effect.  Are you sure you didn't setup a crontab entry that accidentally deleted everything in your home directory?

---

### Post by vdawg on 2008-07-09
oh **** you are right, I ran rm -rf * somewhere in my backup script

---

