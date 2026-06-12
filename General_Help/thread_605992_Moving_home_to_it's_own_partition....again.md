---
title: "Moving home to it's own partition....again"
date: 2007-11-07
forum: General Help
---

### Post by Hagar55 on 2007-11-07
Last time I installed 7.04 and moved my home to it's own partition using this guide:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Now I installed 7.10 and I'm running into all kinds of errors is I try to follow this guide again.

Has something changed in the release that warrants changes to the procedure ?

Also since I needed to start from scratch after my install packed up and died because I made a bad change, are there any good backup solutions for ext3 partitions ?
I use Ghost for my windows partitions, but that can't read ext3.

---

### Post by mike555 on 2007-11-08
For backing up you might want to get " AptOnCD " , it backs up what you have installed as for as app's and updates (but not your home folder, or bookmarks , so back them up also ) , then if you need to reinstall you can just put in the CD after basic installion and install your extra's from it .............. when you reinstall be sure to set a place  for  /home   if you want it on a separate  partition (I learned the hard way ) ......

---

### Post by az on 2007-11-08
What kind of problems?

Often, configuration problems can be caused by the .files in your home drive.  Try creating a different user and log in as that user to see if that helps.

The last think you want to do is save your home drive and re-use it, if that's the case.

---

