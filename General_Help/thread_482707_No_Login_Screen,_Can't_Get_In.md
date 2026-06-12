---
title: "No Login Screen, Can't Get In"
date: 2007-06-24
forum: General Help
---

### Post by DarkStarAeon on 2007-06-24
Hi,

 So I accidentally hit switch user instead of logout, then the screen went black, and the little white disc that twirls signifying that the computer is doing something (a.k.a. "thinking") showed on the black screen and stayed like that for 25 minutes until I decided just to shut it down.

Upon reboot I get to the Grub menu (I dual boot Ubuntu Feisty and PC-BSD) it doesn't matter if I select the most recent Ubuntu or previous versions or recovery mode the best I can do is get to a command line and login, but the GUI never starts. If I don't go to the command line I just see the same black screen and twirly I mentioned earlier.

I can login to PC-BSD on my other drive with no issues.

How do I get the login screen to come back for Ubuntu????

---

### Post by DarkStarAeon on 2007-06-24
temporary solution:

when screen is black press: control+alt+F2

login with your username and password in the command line

stop the gdm by entering in: sudo /etc/init.d/gdm stop

then type in: startx

then when the graphically challenged looking window comes up ignore it completely and hit control+alt+F7

ubuntu then loads graphically then you open a terminal and restart gdm by entering: sudo /etc/init.d/gdm restart

*you have to do that otherwise you won't be fixing anything*

now in system > administration > login window ...go to the security tab and select enable auto login and choose your username from the drop down.

then close everything up and restart your computer.

note: when I tried to logout and restart the restart and shut down buttons were missing from the options, so I just opened a terminal and typed in: sudo reboot


what stinks about this fix is that while it works and will get you back in your machine with a gui, you no longer have a login screen and can't password protect your computer. :(

---

### Post by The Wisedude on 2007-06-24
> **DarkStarAeon said:**
> temporary solution:

when screen is black press: control+alt+F2

login with your username and password in the command line

stop the gdm by entering in: sudo /etc/init.d/gdm stop

then type in: startx

then when the graphically challenged looking window comes up ignore it completely and hit control+alt+F7

ubuntu then loads graphically then you open a terminal and restart gdm by entering: sudo /etc/init.d/gdm restart

*you have to do that otherwise you won't be fixing anything*

now in system > administration > login window ...go to the security tab and select enable auto login and choose your username from the drop down.

then close everything up and restart your computer.

note: when I tried to logout and restart the restart and shut down buttons were missing from the options, so I just opened a terminal and typed in: sudo reboot


what stinks about this fix is that while it works and will get you back in your machine with a gui, you no longer have a login screen and can't password protect your computer. :(


System > Admin > Login Window , try that yet?

---

### Post by DarkStarAeon on 2007-06-24
yep, didn't help. You'd think it would. sigh

I think I'm just going to back up my files and install Ubuntu Studio, been curious about it anyway.

---

### Post by The Wisedude on 2007-06-24
> **DarkStarAeon said:**
> yep, didn't help. You'd think it would. sigh

I think I'm just going to back up my files and install Ubuntu Studio, been curious about it anyway.

Did you try the Local tab in "login window" (System >Admin > login window) Try to tick one of the themes.

---

### Post by DarkStarAeon on 2007-06-25
I did, that was one of the first places I tried. 

Thanks for suggestions though I appreciate it.

Turns out this is a reported bug already, so it's not just me. All the stuff that seems like it should fix it doesn't. A few of us have figured out our way back in like how I posted earlier.

Since having a password protected login is important to me I just backed up all my files and installed Ubuntu Studio instead, I like it.

---

### Post by NorthernSuze on 2007-07-22
Hi
My system locked up on screen saver.  I had to power off; on reboot I get the loading Ubuntu screen then "black screen" - monitors are showing power - no hard drive activy.

I have been running dual monitors with ATI 9600XT/Radeon drivers painlessly up to this point.   I tried the above work around but get no response from computer.  startx does not work from command line.

 I restored my  xorg.conf to the next to earliest one backed up,  which should have given me a clone display with horrid refresh rate on one monitor. . . I thought . . . 

Since this happened after the "rude" shut down, is there a corrupted file some wheres that keeps Ubuntu continuing to the log in screen? Is there an error log I can access that might reveal its problem?

The Xog.0.log has two WW's (I have no idea if these existed before the lock-up - if it ain't broke you don't check error logs!)

open ACPI failed  /var/run/acpid.socket not found
AIGLX: 3D drivers claims not to support visual 0x23 , etc

If anyone can shed any light on this . . . . 
Suzanne
Fiesty 7.04/ASUS A7N8X/ ATI 9600XT radeon os drivers/ (let me know if you need more data)

EDITED - found my problem at least -  the old ATI card finally gave up and died.  So I'm back to figuring out the special touch for my Matrox G550!  :D

---

