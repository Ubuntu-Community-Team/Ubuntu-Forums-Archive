---
title: "Anyone know a good removable media indexing utility"
date: 2007-05-19
forum: General Help
---

### Post by alexhawdon on 2007-05-19
I'm looking for a program that will index the contents of my removable media (CDs and DVDs), so I can search or view their contents without having to load the media.  

Ideally I want it to reference the disks by names that I assign when I have it index the media, so I can scan it then write a number on it and stick it in a folder, rather then referencing the disks based on the volume name, which is often meaningless.

Preferably something that integrates with Nautilus or even the GnomeVFS somehow would be cool...

I've had a bit of a google and a search on synaptic but can't turn anything up, but there must be something!  Would be nice if they could build this feature into the next-gen search tools like Beagle.  I did look but that capability isn't advertised if it is available - please advise if I missed something there.

Thanks in advance folks

Alex

---

### Post by Death_Sargent on 2007-05-19
i wrote a program in shell script that does this with usb drives. 

you could rewrite it to do what your talking about for a disk

---

### Post by fjf on 2007-05-19
CD bank cataloguer is a good windoze application that runs well on wine.  If anyone know an alternative on linux I would give it a try!.

---

### Post by alexhawdon on 2007-06-12
Right, nothing forthcoming and I've yet to find anything so I've decided to hack up a little script to do what I want.    I'll post it here when I've done...

---

### Post by TravMan63 on 2007-06-12
Cathy runs on windows - try it in wine... (I haven't yet) - works on internal HD's as well as removeable optical media.  Haven't tried it on USB/flash yet.


I've used this lightweight (<60KB) FAST indexing / cataloging program for years - have well over 100,000 files indexed with it.

[http://www.snapfiles.com/opinions/Cathy/Cathy.html](http://www.snapfiles.com/opinions/Cathy/Cathy.html)

TM

---edit
[http://www.mtg.sk/rva/](http://www.mtg.sk/rva/)

---edit 2 2007/6/29
Testing on wine is a GO! works fine! (after importing mfc42.dll from an xp install to the system 32 folder)
well,,, it doesn't have the shading and the lines to separate each entry... I successfully imported my usb drive, and a folder on my NTFS XP system volume...

It stores the (tiny) database files in the 'home' directory 

All this was performed on UbuntuCE 7.04 Live CD...

I do challenge anyone to show me a faster native application - I'd like to see it!

---

### Post by meho_r on 2008-01-08
I've found cdcat and Gnome Catalog. cdcat is nice, but pretty old and I don't know if it's developed anymore. Gnome Catalog is to "spartan" ;)

Anyone knows more of them?

---

