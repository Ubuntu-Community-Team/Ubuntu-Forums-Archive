---
title: "Hello all, I'm new."
date: 2007-05-21
forum: General Help
---

### Post by Kogitsune on 2007-05-21
Hello all, I've recently made the switch from Windows to Ubuntu. I'm new to Linux in general, and would like to apologize in advance if I ask any redundant questions, but a few small problems have come up with Ubuntu, and I was wondering if you guys might be able to help me out.

Right, how to explain my first problem... I haven't changed any of my hardware since I switched from Windows to Linux. I hope that doesn't become an issue, but I think it's going to, so I'll put that in the open as something of a disclaimer.
**My monitor refuses to display above the resolution 640x480.** With the help of one of my friends, I've managed to learn how to get to that nice little place he calls "x" via ctrl+alt+F1 and change back and forth between the video drivers "vesa" (which I believe is the default) and a driver called "i810".

While my video driver is set to "vesa", my friend is able to modify pieces of a file called xorg.conf. When he does this, he's able to change my screen resolution to something a little more usable, but he always likes to throw in comments about how bad vesa is, and has managed to drop enough subliminal messages to convince me into staying in i810. The downside to this selection is the very small screen resolution, although he says that the i810 driver is better. I can't see a difference, but I know my monitor is capable of much more than what it's currently displaying. Because of that, **I've tried to force my monitor into a higher resolution by going into xorg.conf and getting rid of all resolutions below those which use 1024x768.**

**It still displays in 640x480.** I've killed and restarted gdm multiple times, poking at different pieces of xorg.conf, but to no avail. 

I believe there may be another file somewhere causing this to happen, but have no idea where to look for it, or even how to start looking for it. 

Help with this one would be appreciated. All I've managed to do is figure out how to get my mouse to display the pointer in two places at once. >.<


Right, that one out in the open, I've got one more issue...

Being a **starcraft** player, I've found that **when an attempt is made to connect to battle.net, the program crashes**. I run starcraft through wine, and I'm unsure of whether or not it's wine crashing or starcraft crashing, but either way, as soon as I attempt to get online, my starcraft window is replaced by my desktop.

I can play single player, but **even at maximum game speed, there's pretty bad lag on my computer.** One of my friends keeps telling me that it's my graphics card, but I fail to see how my card could be the problem when it was working fine in Windows with the same program.

I realize that windows and linux are very different, and that my graphics card might work differently because of that. If that makes his assumption about my graphics card correct, then I might have to get another computer for gaming...

---

### Post by steefjeqv on 2007-05-21
Hi Kogitsune,

Open up your terminal and use the following command :

sudo dpkg-reconfigure xserver-xorg

This will allow you to reconfigure all your settings (mouse, keyboard, ......) so be careful. 
When using this command you can also choose your graphics driver and the resolution.
Just use your space bar to indicate the resolutions needed.

Greetings,
Steven

---

### Post by spin2cool on 2007-05-21
Post the contents of your xorg.conf file so we can take a look at it.

---

### Post by Kogitsune on 2007-05-21
Problem solved. Thanks.
Anyone have a fix for the issue with Starcraft?

---

### Post by ghell on 2007-05-21
If you can get your graphics driver working properly, your starcraft should get a huge performance boost. Without drivers you may as well not have a graphics card as far as I am aware.

I don't know about starcraft and battle.net. I haven't used battle.net since warcraft 2 and I havent played starcraft since I finished the single player when it first came out.

By the way there is nothing wrong with vesa (I think) it's just very old.

---

