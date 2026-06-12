---
title: "Asus Z96j problems"
date: 2007-02-21
forum: General Help
---

### Post by wettestwillie on 2007-02-21
I have an Asus Z96j laptop that im trying to install ubuntu on. When I first got the laptop I installed XP and duel booted ubuntu and it worked fine. I reformatted my hard drive and now when I try to run the live cd theres some graphical problem and when it gets into the desktop its just a bunch of thin lines going diagonal across the screen. when i move the mouse one of the lines moves a little :P. you can kinda tell where the menu bars are because the colors differ a little but but its imposable to navigate around to change any settings or install other drivers or anything. I understand that some distros just don't support the video card but it worked the first time and now it doesn't. opensuse and mandriva work fine.

---

### Post by cronholio on 2007-02-21
You can try to run the Live CD in safe graphics mode. It is the second option in the boot menu. Then after you installed the system be sure to install the proper driver for your card (IIRC, this model has Nvidia).

---

### Post by wettestwillie on 2007-02-21
safe graphics mode does the same thing. and its not nvidia its an radeon x1600 mobile.

---

### Post by mrfuzzemz on 2007-02-23
I'm replying here from an Ubuntu Edgy installation from a Z96J.  I am very familiar with that problem so I can fix it for you. Just do as I say:

Turn on the computer with the live cd in the drive
When it gets to the first screen (Start or Install Ubuntu, boot safe graphics... all of those options) you are going to want to press the corresponding function key for "More Boot Options (F6 or F5, I forget exactly which, but it is listed on the bottom of the screen)
It will then allow you to edit the boot parameters. Just remove the part that says "quiet" and press enter.
You may still get the jumbled graphics and if/when you do press control+alt+F1
Press enter and you should get a command line. Type this in:
```
sudo dpkg-reconfigure xserver-xorg
```
Use the defaults for most of these, but be sure to select the VESA driver and 1024x768 resolution.
You should now be able to boot and install. You will have a very big and ugly resolution, but then you just have to enable the fglrx (ati's proprietary driver) to get the full WSXGA+ beauty.

If you have any questions about any steps here just hit me back.
And in case you need help with the fglrx installation after you have your Edgy installation visit this guide--I find it works best:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

---

### Post by wettestwillie on 2007-02-24
THANK YOU! You have no clue how much I appreciate your help. It's such a relief to find another z96 user with the same problem as me. I gave up on Ubuntu because of that problem and started using Freespire but now that its fixed I'll be using Ubuntu as my main OS. :D

---

### Post by mrfuzzemz on 2007-02-24
Excellent! That's good to hear.  I'm glad I could be of some help!

---

### Post by anfractuosities on 2007-04-11
HELP!  I nstalled fglrx and now the bars on top and bottom of my screen are blank, except for trash.  im on a z96j.

---

### Post by cronholio on 2007-04-13
It seems strange that this should be related to fglrx, but you can add all the elements again by right-clicking on a panel, then select "Add to panel" and move everything to the right position.

---

