---
title: "How to change screen resolution without video"
date: 2020-01-24
forum: General Help
---

### Post by cj8281 on 2020-01-24
My desktop is just disjointed lines.  I need a step by step on how to change the screen resolution back to 1024x768 without being able to see on the screen.

Hardware: Dell Poweredge T110 II, on board video, single 500gb hard drive, 16gb ram, i3 processor, no cards installed.
Software: Ubuntu server 18.04 with file server option and KDE desktop.  

I loaded the server OS and the screen was shifted way to the left, monitor would not adjust far enough to view the left edge.  After reading a bit I decided to add KDE desktop gui to correct the problem and it did.  Until I changed the screen resolution from 1024x768 to 800x600.  The screen went all wonky and so I waited and waited but it did not revert back   I guess it doesn't have a "Do you want to keep this resolution" option.  I was able to shut it down by pressing control alt delete and then hitting the enter key.  That brought it back to the User login screen which I can see just fine.  Upon restarting I chose the second option to repair and went into what I assume to be a safe mode.  Resolution was 640x480 but the resolution couldn't be changed there.  Restarted the machine and entered my password and ...... the screen is still wonky.  I tried a couple other monitors on it but they all show the same thing.  Did the same shutdown again and powered it off.  So, am I just screwed and need to reinstall and start over or does someone have an exact push this button tab 3 times type this and that and hit enter to fix this?
Thank you in advanced.

---

### Post by CelticWarrior on 2020-01-24
The [tech specs]("https://www.dell.com/bo/en/business/p/poweredge-t110-2/pd") show a Matrox G200eW.

Regarding this graphics card: [http://manpages.ubuntu.com/manpages/eoan/en/man4/mga.4.html](http://manpages.ubuntu.com/manpages/eoan/en/man4/mga.4.html)

Try CTRL+ALT+F1...3 to get a TTY that should work.

---

### Post by hurtstotalktoyou on 2020-01-24
You can use ALT-F2 and type "terminal" (then enter).  This should open a terminal, and then you can use command line to change the resolution.

[This](https://askubuntu.com/questions/281509/how-do-i-change-the-screen-resolution-using-ubuntu-command-line) looks promising, but you'll probably have to experiment with different commands to get it to work.

---

### Post by cj8281 on 2020-01-25
I tried to open the terminal but it still was not visible.  I ended up installing an ATI Radeon 3450 video card.  This also helped out on the startup section as it is no longer all shifted to the left.

---

