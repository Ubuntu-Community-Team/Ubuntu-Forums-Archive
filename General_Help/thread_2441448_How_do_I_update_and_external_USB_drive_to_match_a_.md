---
title: "How do I update and external USB drive to match a folder on my computer in Linux?"
date: 2020-04-23
forum: General Help
---

### Post by Brent_Santin on 2020-04-23
I have a master directory of my music library (mp3 files) on my desktop computer. Sometimes I update it or make tweaks to it as I get new music, or fix mp3 tags, etc.
In both my cars, I have copies of this folder on USB sticks so I can listen to the music.  The way I have been updating my USB sticks is to blank them and make a new copy of the Master directory on them. But seeing as my music library is large (about 60GB of data) and the changes I make are only ever a small fraction of this, it seems very inefficient and copying over all that data twice takes a very long time.

Is there a tool in Linux that would allow me to update the USB sticks so that they match the master directory. Something that would "see" the differences between the Master and the USB folder and make only those changes to the USB copies that are necessary?

Thanks,

---

### Post by dragonfly41 on 2020-04-23
[COLOR=#000000]> Something that would "see" the differences between the Master and the USB folder and make only those changes to the USB copies that are necessary?

You may not realise it but you hit on the correct keyword - "differences".

Explore tools such as rsync and rdiff-backup and others designed to backup changes or differences.
A quick search for "backup differences" will reveal articles.[/COLOR]

---

### Post by Brent_Santin on 2020-04-23
Thanks. I should have mentioned, I'd prefer something with a GUI if possible, but can do command line if I must.
Also, I was hoping to not get into a whole backup manager, as I only need the software for just this one purpose.  Like something that could backup a whole network of files would be overkill for my purposes, so was hoping someone could suggest something simple and light.  I will search for the keywords you suggested, too.

---

### Post by HermanAB on 2020-04-23
Rsync is a better kind of copy.  Read the man page and play with it a bit. you won't be sorry.

---

### Post by dragonfly41 on 2020-04-23
[COLOR=#000000]> I'd prefer something with a GUI if possible, but can do command line if I must.

As @Herman writes .. Rsync by command line  .. but also explore Grsync the GUI version which also gives as output the rsync command line.[/COLOR]

---

### Post by Dennis N on 2020-04-23
The copy command (cp) has an option (u) that will copy only files that are newer in the source folder than in the destination folder, or don't exist in the destination. Together with an 'r' option for copying subfolders as well, it's probably sufficient for what you want.

---

### Post by garyed on 2020-04-23
I would recommend putting the command you decide to use in a shell script & put it on your desktop so you can just click on it to do your backups. If all your USB stcks have the same label that would make it easy but you could use a variable like $1 instead for the path.

---

