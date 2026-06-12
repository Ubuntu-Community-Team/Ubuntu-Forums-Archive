---
title: "Can't create ISOs from audio CDs"
date: 2007-02-14
forum: General Help
---

### Post by sicofante on 2007-02-14
Hi,

I'm having a problem copying audio CDs. Once the CD is loaded I just select "Copy disc" from the right clic menu and proceed. The operation is very easy and simple but it's only working for data CDs. When I try to copy an audio CD I get a coaster. Tired of wasting CDs, I've been just trying to create a simple ISO and I've found the same: the ISO is created fine with data CDs but the ones created from audio CDs are corrupted. They seem to be of the right size, but I simply can't open or record them to a blank CD. 

Is there any explanation for this?

EDIT: I just tried a couple of DVDs and they create ISOs fine too.

---

### Post by ghandi69_ on 2007-02-14
Some more information will be needed...

Are you using a program like k9copy or some other app to do this?

Or are you using the command line the "dd" command to create your .iso file.

---

### Post by sicofante on 2007-02-14
I'm simply pointing to the mounted CD that appears on the desktop, right click and choose "Copy disc" from the menu (actually my menus are in Spanish but I believe the English version is saying that).

No command line whatsoever, not even launching any specific application. Pure point and click with the default Gnome interface.

---

### Post by ghandi69_ on 2007-02-15
ok.. I'm not sure about the just using plain ol gnome... but how I do it is using k9copy

sudo apt-get install k9copy

then you want to make sure you have support for mp3... which you can do by following the starters guide..

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

the guide also has a section for copying mp3's I believe.

So I would follow the guide.. using k9copy... and if your still having problems.. come back here.

---

### Post by MetalMusicAddict on 2007-02-15
Yeah. dd doesnt work. A audio CD is different tha a data CD. I dont know if you can make a .iso from one. Ive only ever see app-specific images.

Ill be watching this thread. ;)

---

### Post by sicofante on 2007-02-15
I've been looking around and this seems to be a "bug" in Gnome.

[http://www.linuxquestions.org/questions/showthread.php?t=506664](http://www.linuxquestions.org/questions/showthread.php?t=506664)

[http://ubuntuforums.org/showthread.php?t=93177&highlight=cd+copying](http://ubuntuforums.org/showthread.php?t=93177&highlight=cd+copying)

I understand this is related to audio CDs not having an ISO file system, but that's a poor excuse from a design point of view. "Copy Disc" means "copy disc", not "copy any disc but audio discs"... :-(

I've been really set back by this design flaw. As a matter of fact I've been bragging about this *right-click->Copy Disc* feature of Gnome's in front of some Windows fans, and now I'll have to swallow my proud words... Any ideas on where to push the developers to fix it?

(Also, any suggestions on how to copy an audio CD without going through the hassle of ripping and creating a new audio CD in Serpentine?)

---

### Post by MetalMusicAddict on 2007-02-15
> **sicofante said:**
> Also, any suggestions on how to copy an audio CD without going through the hassle of ripping and creating a new audio CD in Serpentine?

Some of the full-on burning apps should do it but I know of none that make a .iso.

---

### Post by sicofante on 2007-02-15
Actually, the right-click thing does make an ISO file and it's placed in the file system along with a TOC file (no idea why this would be needed at all, but anyway). How to burn that ISO file is the question.

EDIT: Now this is surprising. I've found the following in the Gnome 2.12 release notes:[INDENT]*GNOME's simple CD-burning feature can now copy Audio CDs as well as data CDs. Just right-click on the CD after inserting it.*
[/INDENT]([http://www.gnome.org/start/2.12/notes/en/rnusers.html)]("http://www.gnome.org/start/2.12/notes/en/rnusers.html%29")*. *I'll try tomorrow in openSuse to see if this is just Ubuntu's Gnome.

---

### Post by MetalMusicAddict on 2007-02-15
> **sicofante said:**
> Actually, the right-click thing does make an ISO file and it's placed in the file system along with a TOC file (no idea why this would be needed at all, but anyway). How to burn that ISO file is the question.

Where does it dump the image to?

---

### Post by sicofante on 2007-02-15
You are asked for the place you want it to. I've used both the Desktop and my home folder. (Please check my edit on my previous post)

---

### Post by MetalMusicAddict on 2007-02-15
> **sicofante said:**
> You are asked for the place you want it to. I've used both the Desktop and my home folder. (Please check my edit on my previous post)

Crap. I totally missed it. doh!

I actually think you cant make a .iso from a audio disk. I have to look more into it. I think its why we cant burn the image. Or... The burning apps arent the .TOC file and the Nautilus app does?

---

### Post by MetalMusicAddict on 2007-02-16
Give a look [HERE]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+CD-IMAGES").

Has some info about making images from audio CDs.

---

