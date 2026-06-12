---
title: "Root partition full after upgrade"
date: 2005-10-21
forum: General Help
---

### Post by hanspb on 2005-10-21
I upgraded from Hoary to Breezy the other day using apt-get. Afterwards everything seemed fine (or most things anyway). I played around a lot, logged on to different users, rebooted, everything ok. Then today I could suddenly not log in to any users. Also failsafe Gnome was impossible. I got an error message containing contents of the ~/.xsession-errors file, of which this seemed to be the crucial bit:

```
mkdtemp: private socket dir: No space left on device
```

So I fired up my Ubuntu live cd and I found out that the root partition was full!:confused: 
This is a 3.42 GB partition, which has always had plenty of space, so I wonder what has happened now? Are all the files from the Breezy installation there in addition to the ones from Hoary or what? Something must be filling up my system.
I got the impression that with Ubuntu one could install once and then just upgrade into eternity more or less, in order to always have an updated system, as opposed to other systems where you have to format and do a full reinstall with all the trouble that gives you. Well it seems not!

So, can anyone help me, please???

:smile: 

Hans Petter

---

### Post by Ocxic on 2005-10-21
[QUOTE=hanspb]I upgraded from Hoary to Breezy the other day using apt-get. Afterwards everything seemed fine (or most things anyway). I played around a lot, logged on to different users, rebooted, everything ok. Then today I could suddenly not log in to any users. Also failsafe Gnome was impossible. I got an error message containing contents of the ~/.xsession-errors file, of which this seemed to be the crucial bit:

```
mkdtemp: private socket dir: No space left on device
```

So I fired up my Ubuntu live cd and I found out that the root partition was full!:confused: 
This is a 3.42 GB partition, which has always had plenty of space, so I wonder what has happened now? Are all the files from the Breezy installation there in addition to the ones from Hoary or what? Something must be filling up my system.
I got the impression that with Ubuntu one could install once and then just upgrade into eternity more or less, in order to always have an updated system, as opposed to other systems where you have to format and do a full reinstall with all the trouble that gives you. Well it seems not!

So, can anyone help me, please???

:smile: 

Hans Petter[/QUOTE]


try getting so partioning software and resizing the partition,, becareful and read the documentation to see if you will possible lose anything on the other partitions, 
or just reinstall... or if someone has a better suggestion then do that. consider this a last resort.

---

### Post by kozimodo on 2005-10-21
Try emptying /var/cache/apt/archives.  It's probably full of .deb files for various updates.

---

### Post by hanspb on 2005-10-21
It was, thanks, but the partition is still listed as full when I do a "df" after I delete all of the .deb files. Even if I open a new Nautilus it says "free space 0 bytes".

Edit:
I guess there must be some free space if I want to do anything, so nothing will be deleted as long as the partition is completely full. Then my only option is a full reinstall... oh dear!

---

