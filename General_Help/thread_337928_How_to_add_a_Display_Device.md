---
title: "How to add a Display Device?"
date: 2007-01-13
forum: General Help
---

### Post by Goluxas on 2007-01-13
Today my motherboard finally decided, after a few years of fluctuation, to cut all ties with my video card.  I knew it would happen, and it finally did.  At least, that's what I think is happening, by my own diagnosis.  

In both Windows XP and Ubuntu, I would start up and get to the point where I wanted to do something like, say, open Firefox.  I would click the button, and the screen would freeze after a few seconds, before the window would display.  In XP, the ATI VPU Recover dialog would pop up and reset the card, to keep the system from freezing, but in Ubuntu, I have no equivalent program, so it would just freeze until I rebooted the machine manually.  So, I have since removed the video card in order to avoid this error.  So far it's worked... in XP.

But I understand that.  That is not the problem.  The problem is this:

I have no GUI in Ubuntu.  Apparently the video card was the only recognized display device in Ubuntu, so now that it's gone, I can't display the desktop or any GUI programs.  I am presented with a terminal screen to login with, and then I can do anything that does not require a display.

When I type "startx", it tries, and then gives an error of "No display device found" (or something similar).

I guess what I want is a way to make Ubuntu realize that I'm using the built-in display output from the motherboard.  Preferably in a way that can be done from the command line, since that's all I can use.

By the way, I'm using Ubuntu 6.06 LTS, I think (I know that it's Dapper Drake), and an ASUS motherboard with model number "A7V8X-MX".  If you need any more information, just ask.

Thank you all for your help.

---

### Post by ajmorris on 2007-01-13
can you post your xorg.conf please? /etc/X11

since you have not GUI and if you display the page in a terminal then you can't copy all of it. Can you possibly upload your xorg.conf file? If it says you can't upload rename it to xorg.txt (but not the one in /etc/X11, because that needs to be kept as xorg.conf, so just copy it to another folder and rename it.)

---

### Post by jocko on 2007-01-13
If I'm not wrong, that motherboard has an integrated VIA video card.
Try running this command:
```
sudo dpkg-reconfigure xserver-xorg
```
In the first screen, scroll down the list and select a driver with "via" in it's name (I don't know the exact name of it).

---

### Post by Goluxas on 2007-01-13
Ah, thank you.  The dpkg-reconfigure command worked perfectly.

---

