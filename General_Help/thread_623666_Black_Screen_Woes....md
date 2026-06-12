---
title: "Black Screen Woes..."
date: 2007-11-26
forum: General Help
---

### Post by sukhoi on 2007-11-26
Hey guys, I've been having a bit of a problem. I've searched and searched all over the boards for a solution to this and either no one knows or nothing to seems to work. I guess I'll start by laying out the facts.

My setup:
Intel celeron 2.4ghz
1.5ghz of RAM
120GB HDD as master
80gb HDD as slave
Nvidia BFG 6800 GT with dual monitor outputs. DVI->VGA converter on left screen.
Mouse
keyboard,
etc

The Issue:
Had a perfectly good running install of Gutsy working. Went on vacation for a week, turned desktop off to conserve power. Came back from vacation and when I boot up my desktop I presented with a black screen and a small X for a mouse. Keyboard freeze, capslocks and keys don't work. Mouse doesn't move, no HDD usage or anything. 

Odd I thought.

Being the Linux noob I am. I boot into windows to search ubuntu forums for a quick fix. 
Windows gives me a blue screen. Awesome, HDD failure after sitting still for a week I'm guessing.

I clear both drives. Nothing important on them worth trying to salvage. Go with a fresh install of Gutsy. Install goes fine. Boot up takes forever and a nice black screen and X mouse greets me again. Super weird, that's never happened before. I boot into recovery mode to try to reconfigure the Xserver via **dpkg-reconfigure xserver-xog**.Scrolled down to my video card in the xorg.conf,  Changed drivers to Nvidia. Black screen on boot. Changed Driver to nv: black screen on boot. Changed driver to vesa. Boots fine, still takes 10 minutes at the least to get to the login screen. I try to work with Envy to install my Nvidia drivers for me. Reboots to a black screen and X mouse. I try various quick fixes around the forums, reinstall and say,

I'll just go back to Feisty.
Stick in the live cd, install goes great. Take disk out, reboot. Black screen and X mouse, my familiar best friend. Repeat what I've done in gutsy a few dozen times. I'm running vesa drivers on one monitor and there's nowhere for me to go now. Everything i try gives me a lovely black screen. I'm thinking of going to Edgy but if Gutsy and Feisty and giving me all this trouble now when they worked perfectly before then I wouldn't even know what to do if Edgy gave me the same issue.

If you guys have any advice or some idea's to throw out there I'd reall appreciate it. I'm tearing my hair out trying to figure out why all of sudden nothing wants to work correctly when it was just fine last week.

---

### Post by Arwen on 2007-11-26
Since XP and ubuntu both won't boot properly it's probably hardware problem.
Supposing both hds are OK,on which one did you try to install ubuntu?
When you type > startx or > sudo gdmon that black screen,you get nothing?GDM is supposed to run automatically when you boot ubuntu(you can set that by changing /etc/conf.d/xdm: write DISPLAYMANAGER="gdm" in the line that says DISPLAYMANAGER)
Good luck!

---

### Post by sukhoi on 2007-11-26
Thank you for the reply!

I've installed Ubuntu on my 120gb Drive. The 80gb is the slave drive. I can't type in any commands or Alt+CTRL+F1 to a terminal because the board and whole desktop is frozen. If I enter Startx from recovery mode I get a error "Failed to initialize HAL" once in a while. 

The Motherboard posts and goes through diagnostics. Grub loads and I can choose my kernal version or other OS. Then the ever ominous loading bar appears and sits there for about 10 minutes before fully loading. Afterwards I'm greeted with a black screen and X mouse with a completely frozen system. Changing Drivers to Vesa completely fixes everything, =\ Ubuntu just doesn't like my nvidia drivers and card..

---

