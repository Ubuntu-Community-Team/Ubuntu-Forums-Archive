---
title: "Strange file system problem i need help with..."
date: 2007-09-01
forum: General Help
---

### Post by n8y on 2007-09-01
This isn't necessarily a linux problem, but I hope someone can help me anyways.

Ok so I'm in a bit of a bind. I backed up a whole bunch of files from my parents computer to their second hard drive, which was set up using some sort of western digital tools. I do what i do on my own system and copy all the files i want to keep to a secondary hd and then while I redo the operating system I unplug that second hard drive to make sure nothing gets lost. But now I have the problem that windows won't recognize that there are files on it.  
 
Windows recognizes the drive itself, but can't seem to read it or recognize the file system it is using. The Western Digital data lifegaurd tools recognizes the drive and that it has files on it, but the only way it wants to "initialize" the drive is to erase it. Is there any way to save the information on this drive?? It's a 200gig western digital drive on windows XP home.

Now I've tried to access the drive using linux and that won't work either. Both windows and linux are saying it's using some unrecognized file system. How can this be??!?! Just before i reformatted I was copying files to the drive inside of windows. what could have happened to the file system? how could it have been so different that now it won't recognize it? Does anyone know of anyway to recover the files? any program to use?

---

### Post by merlinus on 2007-09-01
Did you pull the plug on the drive without unmounting it?  That may be at least part of the problem, if so.

You might try systemrescuecd, which has lots of excellent tools for recovering data and partitions.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

-merlin

---

