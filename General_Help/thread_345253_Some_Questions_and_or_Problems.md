---
title: "Some Questions and or Problems"
date: 2007-01-24
forum: General Help
---

### Post by Goober on 2007-01-24
It evidently has been a long time since I last used Linux, and thus I have forgotten many things ... I have run into a number of issues with programs not working for me, and I am wondering how to get them working the way I want ... 

1 - I have tried to install some programs, such as mplayer, but could not, and get some error messages.  I recall, back in my Breezy days, that you had to do something in the Terminal first, enabling repositories or something in order to install certain programs ... is that the case?  If so, how do I do this?

2 - I have the Microsoft Mouse, the one with the little scrolly thingie in the middle.  I recall in Windows, when you press down on the scroll thingie, you can scroll much faster.  How do I enable that?

3 - In Windows, I used to play movies directly online, YouTube, and other such sites.  How do I do that in Linux?  I recall it being some sort of Mozilla plug-in, with some sort of player, but I forget exactly which one it was.

4 - DVDs.  I noticed that I can play MP3 files, and .avi video clips, but how do I enable DVDs to play?  I have VLC, and use that program for most of my multimedia (love it!), but it won't play DVDs.  Also, my computer does not seem to recognize my DVD drive.  It recognizes my CDRW, but not the DVD one.  Any suggestions?

I think those are all of my present issues.  If anybody could help me out with them, I'd muchly appreciate it!

Thanks in advance.

---

### Post by thegestetner on 2007-01-24
1. You have to enable the Universe and Multiverse repositories. Open /etc/apt/sources.list in a text editor (for brevity's sake just do, in a terminal: *gksu gedit /etc/apt/sources.list* )
Comment out (remove the #) from the lines that denote those repositories. The file will point these locations out to you. Save (Ctrl-O), quit, and type *sudo apt-get update*. You should be home free at this point.

3+4: Download [Automatix]("http://www.getautomatix.com"). It autom (atically downloads and installs various proprietary components such as DVD support (libdvdcss) and Macromedia Flash, which will solve your YouTube woes.

Sorry, I have no clue about the MS Mouse.

---

### Post by Goober on 2007-01-24
Apparently I already had the Universe and Multiverse repositories enabled ... but if I can get DVDs working on VLC, and play music with RhythmBox, I won't need mplayer anyways ...

Ok, major problem here!  I went through the Automatix2 process, and it successfully took out 41 files, and installed 3.  However, it ran into an error at the very end, and gave me a message to run "Sudo apt-get upgrade -f" or something similar in a Terminal, and that would fix everything.  I can't do that, however, because one of the 41 files it took out was the gnome Terminal program, apparently.  Umm ... HELP!

---

### Post by 23meg on 2007-01-24
> gksu gedit /etc/apt/sources.list )
That has to be ```
gksudo gedit /etc/apt/sources.list
```
> various proprietary components such as DVD support (libdvdcss)Just a note: libdvdcss isn't proprietary, it's GPL'd.

---

### Post by pebo on 2007-01-24
> Ok, major problem here! I went through the Automatix2 process, and it successfully took out 41 files, and installed 3. However, it ran into an error at the very end, and gave me a message to run "Sudo apt-get upgrade -f" or something similar in a Terminal, and that would fix everything. I can't do that, however, because one of the 41 files it took out was the gnome Terminal program, apparently. Umm ... HELP!
Can you get to a virtual console (Control+Alt+f1)?

---

### Post by Goober on 2007-01-24
Ok, somehow Automatix2 has caused some major problems with my Ubuntu Edgy Install.I understand the basics of what Automatix2 is supposed to do, and taking out 41 files does NOT seem to be it.  I can't even log into my Edgy install now, I enter my undername and password, and then nothing happens, it refuses to load.  I tried the Control-Alt-F1, that worked, but I don't really know know how to fix it from there.  I typed in the "sudo apt-get upgrade -f" that Automatix2 installed, and that did something, getting some files installed, and taking out Automatix2, but that did not solve the problem.

I am presently working off the LiveCD.  Would you guys suggest just doing a clean install of Edgy again to get read of the problem, overtop of the old one, or trying to fix the present installation?  A clean install, and then trying again almost seems like the best bet ...

---

### Post by pebo on 2007-01-24
Before you re-install it may be worth trying the following from a virtual console to get your GUI back. First log in using your user name then ```
sudo dpkg-reconfigure xserver-xorg
```hth

---

