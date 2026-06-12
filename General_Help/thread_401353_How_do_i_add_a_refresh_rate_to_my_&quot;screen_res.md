---
title: "How do i add a refresh rate to my &quot;screen resolution&quot; options?"
date: 2007-04-04
forum: General Help
---

### Post by Eduardo Serra on 2007-04-04
When i want to change my screen resolution i can only choose a refresh rate of 85 Hz, and im afraid my computer need a lower one when working with 1280x1024. I have a compaq MV720, and when i select the resolution mentioned above it wont fit on the screen, i presume the refresh rate is the problem, but i don't know how to change it. I already tried adding the HorizSync and VertRefresh lines to my xorg.conf, and it didn't worked.

---

### Post by wonk-o-matic on 2007-04-04
If you haven't already, backup your /etc/xorg.conf file.  

When you look at the Display Settings in the GUI, is your monitor listed as generic, or by the model name?  

What's your video card, and what driver is the system using?

---

### Post by Eduardo Serra on 2007-04-04
All of that information and more can be found here: [http://ubuntuforums.org/showthread.php?t=392803](http://ubuntuforums.org/showthread.php?t=392803) wich is the thread i started weeks ago, when i didn't know what the problem was, now, i just want to now how to add a refresh rate (I say this because of moderators, i just want them to know this is a totally diferent thread).

---

### Post by leroy_30 on 2007-04-21
I had the exact same problem. Compaq Presario MV720 Monitor. Yuck resolution.

Ubuntu reports my onboard video as 82915G/GV/910GL Express Chipset

Here's what I did to fix it.

```
sudo dpkg-reconfigure xserver-xorg
```


Filled in the blanks w/ info from:

[http://support.radioshack.com/support_accessories/doc56/56224.htm]("http://support.radioshack.com/support_accessories/doc56/56224.htm")

Gave the video 65535 (64MB) Ram to play with.

I don't remember what screen it was on but I did enable all of the "what I call video drivers" to load when X starts. Just so I don't have to remember later. LOL.

Logged Out. CTRL-ALT-Backspace.

Logged In. Changed Resolution.

Whammo Blammo!

works like a champ now!

---

