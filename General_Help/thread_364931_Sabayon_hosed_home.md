---
title: "Sabayon hosed /home"
date: 2007-02-18
forum: General Help
---

### Post by jabeez on 2007-02-18
I installed Sabayon on my second hard drive just for kicks because I've heard good things, and during my first install attempt I foolishly had it use my /home partition. That didn't work out too well so I installed again and had it use it's own /home. I toyed around with it a bit, and yeah it's kinda cool but with a gig of ram, a 9700 pro 128mb, and 2gh Athlon the XGL/Beryl is pretty slow. Anywho, I booted back into Kubuntu, and it appears my /home is screwed. My taskbar is all messed up and I'm getting sounds from Sabayon and a really screwed up theme. Anyone have any ideas of a fix or is a fresh install in my future?

---

### Post by jabeez on 2007-02-19
Anyone? I've got a working MythTV install and database that I would like to keep intact?

---

### Post by H3g3m0n on 2007-02-19
Go through and delete the hidden directories in you home folder such as .gnome .gnome2 .kde and anything else you want to reset to default. Alternatively you can just backup the .mythtv directory and delete the rest. Just avoid the . files in your home directory (stick to the . directories) as the files are used for things like bash profiles. Although its possible Sabayon overwrote them too. Its also possible it formatted the partition and erased all your old setting in which case create a new user under Ubuntu.

Gnome/KDE should recreate the directories with the defaults.

---

