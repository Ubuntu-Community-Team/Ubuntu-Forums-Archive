---
title: "How to install a completely new keyboard layout?"
date: 2008-03-26
forum: General Help
---

### Post by sp3ctum on 2008-03-26
Hi. I have a specific (rare) keyboard layout that I'd like to use. It's called das, and more info can be found here:
[http://cristian.seres.fi/DAS_en.html](http://cristian.seres.fi/DAS_en.html)

There are installation instructions, but I can't seem to figure them out properly. Can someone help me?
I'll translate the whole Finnish section about installing on a linux here:

Save das ([http://cristian.seres.fi/das](http://cristian.seres.fi/das) ) as /user/share/X11/symbols/das with root rights (e.g. with sudo) and read the additional instructions from the start of the das file. In addition to that, for Gnome the file /etc/X11/xkb/rules/base.xml needs to be modified. Here's a diff file whose line numbers don't necessarily match: base.xml.diff (save as) (the link is [http://cristian.seres.fi/base.xml.diff](http://cristian.seres.fi/base.xml.diff)). You can also edit the base.xml file by hand with root rights, adapting the diff file. After the changes the DAS layout should appear in the Gnome language settings. This tutorial has been tested in Ubuntu 7.10.

An old tutorial for Linux (an option to the above): an .Xmodmap ([http://cristian.seres.fi/xmodmap](http://cristian.seres.fi/xmodmap)) file has to be copied to the home directory of the user, and it has to be renamed to .Xmodmap. The location of the keys is defined in the file. After this, several Linux versions work with the new keyboard without further tinkering. Removing is done by deleting the same file. If you have an .Xmodmap file beforehand, make a backup of it first. Unlike in Windows, Ctrl + letter and Alt + letter change according to the new layout, which requires some getting used to in cutting and pasteing. Be sure that you have a printed chart of the setup of the keys before you install it. :-)




Okay, that's the info. Can someone please help me with the installation? I tried all those instructions in detail, but they yielded no results. Will probably try again, but I'd appreciate any help a lot anyway.
What's the standard procedure on such a matter, if not the one in the instructions ?

edit: where exactly is the layout supposed to appear in the language settings? Perhaps I didn't see it vefore.

---

### Post by sp3ctum on 2008-03-27
Any ideas? Anyone?
I tried the xmodmap way yesterday, and it worked, but I could no longer use some hotkeys. At first I was able to open the terminal, later on not even that (with a hotkey, I mean).
What was going on?

---

### Post by Kiri on 2008-03-27
Have you tried setting the keyboard model and layout in System>preferences>keyboard>layout ?

I got my Japanese layout working perfect with this (its also quite rare). Also which distro are you using?

---

### Post by sp3ctum on 2008-03-27
I tried that after following the installation instructions, but the layout wouldn't appear under Finnish. I'm now trying to create my own from scratch, or by modifying another file, but it seems odd. :/
I have Ubuntu 7.10.

---

### Post by Kiri on 2008-03-27
On mine I can choose a layout for Finland and there are 4 variations of it also (default, classic, northern saami, mac) . Are none of them suitable?

---

### Post by sp3ctum on 2008-03-27
I see them too, but this layout that I'd like to install is completely new, so it's not there. What I'd like to know is how to get it there.

---

### Post by Kiri on 2008-03-27
Unfortunately I didn't find any easy way to remap keyboard keys when I was trying to get mine working, so I cant really help you there. 
Is it a laptop or external keyboard? 
Have you had it working in other OSes before? And if so, with extra drivers?

How many of your keys are mapped wrong by the way?

---

### Post by sp3ctum on 2008-03-27
Something really odd has happened. I seem to have installed a keyboard layout manager of sorts (without trying to): it's called KDE keyboard module. It recognized my keyboard layout like it was supposed to get recognized earlier. Things work like they're supposed to, now.

Only one problem remains: how can I set the KDE keyboard module to start up when the machine starts up? And should I try to get rid of the old one? It's the gnome default that comes with the standard Ubuntu 7.10 install. I think they're not compatible.

---

### Post by Kiri on 2008-03-27
Not sure about the KDE working in gnome... I guess you can try it. 
As for the startup, if you go to System>Preferences>Sessions you can add it to the list of startup apps

---

