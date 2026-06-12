---
title: "Terminal settings saved where?"
date: 2008-05-13
forum: General Help
---

### Post by apokkalyps on 2008-05-13
I just had to format my Ubuntu to fix some problems it was having and am putting my system back together.  I have my home directory completely backed up with all the hidden folders containing my user settings for various programs.  I've had alot of success restoring the specific settings for certain programs.  But can anyone tell me where the settings for Terminal are saved?   I'm talking about the terminal emulator for gnome.  I wish it was given a different name so there wouldnt be confusion that I mean the gnome program not just the terminal.  But anyway I had it set up really nice with a picture in the background.  It was one of my favorite things about my desktop.  There is no .terminal folder however to copy settings over from.  Can anyone help with this?

Also, where is the config file where you turn on colors by default in bash?

---

### Post by shakabra on 2008-05-13
Open up the terminal and go to edit>current profile.  I think you will find everything you need there.

---

### Post by apokkalyps on 2008-05-13
thanks, but no the point is I dont want to have to rebuild my settings.  I have them backed up.  I found where the settings file is saved, its in
> ~/.gconf/apps/gnome-terminal/
But I keep trying to swap the files out and it changes them back rather than using the new ones.

---

### Post by cylux on 2008-05-13
I'm not sure if it runs the same way, but you can try the ~/.Xresources or ~/.Xdefaults (depending on Ubuntu version) file, I know that that file takes all the settings for the other terminals (aterm, (u)rxvt, xterm etc. etc).

---

### Post by fernandinho on 2010-02-16
hi people,

I've had the same problem recently and after reset all my gnome settings to fix it, I discovered that it was more simple than I had thought.

All gnome-terminal settings can be changed there:

Alt + F2 > gconf-editor > apps > gnome-terminal

any problem with gnome-terminal can be solved there.

I hope that helps.

---

### Post by explainer on 2010-08-08
Thanks for the tip on how to get to gnome-terminal properties.  My problem is that my profile properties are not saved between sessions.  If I shut down and start up again, my profiles are lost. How can I fix that?

---

### Post by hakermania on 2010-11-06
A way to modify the terminal's settings is from gconf-tool-2. E.g. too change the terminal's background image to binary.jpg you give:
gconftool-2 --type string --set /apps/gnome-terminal/profiles/Default/background_image /home/alex/Pictures/binary.jpg

---

### Post by heuvaladao on 2011-08-25
AFTER A LOT OF RESEARCH, THE ANSWER IS SIMPLE:

1. OPEN THE TERMINAL AND PASTE THIS PATH (and hit enter of course):
**~/apps/gnome-terminal/profiles/Default/**

2. IN THIS DIRECTORY YOU WILL FIND A FILE NAMED **%gconf.xml **. THAT`S WHAT UR LOOKING FOR. IT HOLDS ALL YOUR TERMINAL CONFIGS. BACK IT UP OR REPLACE IT FOR A NEW ONE. JUST MAINTAIN THE NAME.

SPREAD THIS. THERE`S REALLY MANY PEOPLE LOOKING FOR THIS.

---

### Post by itagomo on 2012-06-13
in 12.04, it's ~/.gconf/apps/gnome-terminal/profiles/Default/

---

