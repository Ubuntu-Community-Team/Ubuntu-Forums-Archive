---
title: "Resolution problem."
date: 2007-06-04
forum: General Help
---

### Post by FRuMMaGe on 2007-06-04
I have a new laptop which supposedly can have a resolution of 1280 by whatever, but when I look on the Screen Resolution in Ubuntu, the only choice I have is 1024x768 at 60hz.  How do I allow my laptop screen to use it's full resolution?

---

### Post by jimbob on 2007-06-04
What kind of video card/hardware do you have?

You may need to load the Linux restricted modules
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by flowingfire on 2007-06-04
I had a similar problem until I switched my monitor in "Monitor and Display."  I think that changes the xorg.conf configuration file to include other resolutions based on what your monitor is capable of.

Unfortunately I wouldn't know to begin in Gnome, as i'm using KDE... But in KDE, you edit the "Monitor & Display" under the "hardware" tab, then tell it what monitor configuration to use.

---

### Post by Cilionelle on 2007-06-09
After getting fed up with probs in Ubuntu, I switched to KDE.  I would love to know how to get to the "Hardware" tab - is that in the xorg.conf file?  Is there an editor I can use?  I realised that I have to do "su" and my password to move forward, but how do I edit it?  Kedit won't work - something about it not being able to do something in X...  Or is it elsewhere?

My main problem is I am stuck with only the option of 640x480, and it is too small, especially since it seems that KDE doesn't allow full movement of windows...

---

