---
title: "question about wget..."
date: 2015-09-22
forum: General Help
---

### Post by Nixarter on 2015-09-22
the only thing I need to do that I can't figure out with wget is, given the attached basic file structure, download:

A,B,C,C,B,C,C, and so forth

instead of the default method of recursive:

A,B,B,C,C,C,C

In other words, I need to download each folder in level one in its entirety, before moving on to the second level 1 folder.  As opposed to downloading all level one folders and files, before doing the same for level 2, and so on.

I would simply run wget for each folder, but I've made a big mess of my file system (not forward-thinking enough) and I have many thousands of level 1 folders, so that would be practically impossible.

before someone asks and I have to explain anyway... I have a RAID file server that the HDD's are getting old on.  I want to swap it to a much larger and different type of raid system, but I am going to de-raid it first onto smaller drives while i physically upgrade.  I want to wget files until drive one is full, then wget to the second destination drive until it is full... that was files are complete, in order of file name, so I know what data is where easily, and I already have a method of re-building that into a new server in place.  Doing it the other way would be a nightmare since I have to split the drives, and it is not something I want to do.

---

### Post by sudodus on 2015-09-22
Would it be possible for you to use ***rsync*** instead of wget? In that case, try with a small directory tree, if it will do what you want.

If not, maybe you can make some kind of manual system that works exactly like you want: it might be possible with a shell script with a loop for each directory in the first level.

---

### Post by Nixarter on 2015-09-22
I'll look up rsync.  Thanks for the suggestion.

I also considered a shell script,, but I have no script-writing experience at all.  I've never even used them.  I know the general idea of their functions and limitations, but given my "noob-ness" I want to keep that as a last resort.

---

