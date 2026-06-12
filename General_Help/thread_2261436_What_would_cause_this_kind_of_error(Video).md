---
title: "What would cause this kind of error?(Video)"
date: 2015-01-19
forum: General Help
---

### Post by ImTroyMiller on 2015-01-19
This is my latest error I am having.  I am assuming it's a graphics driver issue...

[http://youtu.be/jYlulJbWCd8](http://youtu.be/jYlulJbWCd8)

---

### Post by ImTroyMiller on 2015-01-19
I'm going to give a proprietary driver a try.

It actually runs for hours before crashing and has only crashed twice so far...

---

### Post by deadflowr on 2015-01-19
Not sure, as I have not a lot to go on, but the way the clipping happens it seems more in line with a hardware fault than a software fault.
But again, you don't gives us much to go on...

You don't tell us what the gpu card is.
I cannot tell for certain, but it looks likes a laptop.

The way it clips reminds me of what it looks like on a desktop when display cable is not properly connected to the monitor.
But it's also very short, so it's indeterminate if this is an always happening behavior, or something that happens from time to time.

Again, it could be a software problem, just that it reminds me, with the little bit to go on, of what I have seen with improperly connected hardware setups...

---

### Post by ImTroyMiller on 2015-01-20
Sorry, I should have added more detail.

 This is my desktop PC.  I have three hard drives, one with Ubuntu, one with Windows 7, and one with Kali.  Windows and Kali run fine, so I am assuming that it's not a hardware issue.  Also, it did up crashing after I switched to the proprietary driver.  I tried booting again but it just restarted my PC, so I booted into Windows.

 My specifications...

 64-bit
 AMD FX-6300 Six-Core Processor
 Nvidia GeForce GTX 650 Ti Boost Graphics Card
 16GB RAM

Each hard drive for Windows and Ubuntu are 1TB and I use them entirely for the OS.  Kali is on an 80GB hard drive.

 I do have stereoscopic 3D glasses plugged in, but I don't think Ubuntu has drivers for them.  So maybe those being plugged in are causing some type of issue.

---

### Post by ImTroyMiller on 2015-01-21
This solution posted in a comment to my YouTube video seems to have fixed this issue...

> Is this a Nvidia Graphics Card? There is an issue with Nvidia's latest  divers and Unity+Compiz that causes Compiz to glitch out and corrupt the  screen. If this is the case for you, there are two options. Either  install a Non-Compiz based desktop like Cinnamon, Gnome, ect... or you  can do this in a terminal (alt+ctrl+t to open one):

"sudo apt-get  install compizconfig-settings-manager" and then open Compiz Setting  Manager in the dash and navigate first to "Composite, and check  "Undirect Fullscreen Windows"". Then to "Workarounds, and check "Force  complete redraw on initial damage" AND "Force full screen redraws  (buffer swap) on repaint".

That should fix the tearing. For extra  measure, tough not required, you can also (If you ues a NTSC "60hz  monitor") run this command without quotes in a terminal:

"sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop"

Then  go to "Startup Applications and create a new startup called "Refresh"  and just put whatever in the comment box, but in the command box,  including quotes, put:

sh -c "sleep 10 && dconf write /org/compiz/profiles/unity/plugins/composite/refresh-rate "60" &"

That should fix everything. :)&#65279;

Posted by KitsuneCentral

---

