---
title: "Advice for amarok with large music collections..."
date: 2007-04-30
forum: General Help
---

### Post by Rinnan on 2007-04-30
I had problems with amarok and a largish music collection, about 3,000 songs.  

It was very slow to update, or rescan the collection.  It also crashed while rescanning or updating if it was also playing a song.  This is fairly routine for me, since I'm constantly adding music and also playing it (big fan of amarok).

Basically, use postgres instead of SQLite.  After I changed database backends, everything "just worked" -- and a whole lot faster!

[http://amarok.kde.org/wiki/Postgresql_HowTo](http://amarok.kde.org/wiki/Postgresql_HowTo)

:guitar:

---

### Post by tcpip4lyfe on 2007-04-30
Awesome.  Good info

---

### Post by musicinmybrain on 2007-04-30
Interesting. I have a library of ~4600 files in FLAC format, and I've wondered if switching databases would be worthwhile. I've heard mixed things elsewhere. Glad to hear it worked for you!

---

### Post by I_Like_Pie on 2007-11-01
Not to steal your fire, but I am running Amarok 1.4 in Gutsy using SQLite.
 
It must be a lot better than previous versions as I have 200gig containing about 50,000 songs and it works just fine.  Speedy and responsive.
 
Posgre and MySQL are great because they are portable, but the default database is pretty strong these days.

---

### Post by FSHero on 2007-11-17
> **I_Like_Pie said:**
> Not to steal your fire, but I am running Amarok 1.4 in Gutsy using SQLite.
 
It must be a lot better than previous versions as I have 200gig containing about 50,000 songs and it works just fine.  Speedy and responsive.
 
Posgre and MySQL are great because they are portable, but the default database is pretty strong these days.

Gaah! For some reason, my friend has slow-downs even while using MySQL! Here are some version numbers:
```

Qt: 3.3.7
KDE: 3.5.6
Amarok: 1.4.5
MySQL: mysql  Ver 14.12 Distrib 5.0.38, for pc-linux-gnu (i486) using readline 5.2
Kubuntu: 7.04

```

He has a collection on my computer, which we share. The specs are:
Processor: Pentium 4 3.4GHz with Hyper-threading
RAM: 512 MB DDR1
Graphics card: NVIDIA Geforce 6700XL, using the proprietary video drivers
(I think that this is sufficient information.)

So... basically, once upon a time, I set up a MySQL collection for him. Before this, using SQLite, Amarok was often unresponsive, and searching for a song name took many seconds (if not 1-2 minutes). It all went fine at first. It was responsive, etc.

But now, when he starts Amarok, he often has to wait for *two minutes* before the Amarok window actually came up. (I also had this problem in one session but it seems to have gone now. I have about 300 files in my collection.)

When the window does come up, the bottom of the windows says something like "updating collection", and takes a few seconds. It then stops at 68% and stops responding (e.g. when trying to click on a new song).

I tried to run it just now from Konsole, but it hasn't even brought up the Amarok main window. The output is attached. (Please ignore the "ps aux |grep amarok" line -- I was about to kill the process, but typed in the wrong window!)

He has a collection with 3434 files. I found this out by navigating the his collection's root directory, then running:
$ find . > temp.txt
I counted how many lines there were in Kate.

I don't know if the following is relevant, but: a couple of days ago, Adept updater offered me an update, which included:
libsmbclient
samba
samba-common
smbclient

However, it failed (I can't remember the exact error message.) I'm getting a similar problem [as described here](http://ubuntuforums.org/showthread.php?t=615552&highlight=403+forbidden).

Can anyone help please?
I will try the following to see if it works: I will delete my friend's amarok database using sql commands. I will create a new one, and enter its details into Amarok.

---

### Post by FSHero on 2007-11-18
I should have mentioned this: the /var/lib/mysql/myfriend_amarok folder (which contains the database files) was 3GB in size. (Yes, **3 gigabytes**, whereas my own database's folder was under a megabyte.)

In particular the images.MYD file in the myfriend_amarok folder was about 900 MB alone.

Anyhow, I did what I said I was going to do. I recreated a new database, then went to Amarok and set it to watch no folders. I entered the database details (login, etc.) and selected a couple of folders to watch.

I think the problem may have been because my friend's Amarok was watching multiple folders, and I had lost track of how many he was watching. This time, I know it is a lot fewer.

The new myfriend_amarok folder is just 3.1 MB. Good news, I guess! If I remember, I'll report back to tell if everything is still going fine.

---

