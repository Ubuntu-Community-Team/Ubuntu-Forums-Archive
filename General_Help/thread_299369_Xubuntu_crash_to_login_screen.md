---
title: "Xubuntu crash to login screen"
date: 2006-11-14
forum: General Help
---

### Post by Unisyst on 2006-11-14
Hi, I posted in another forum about this but got no response.. 

Xubuntu keeps crashing to the login screen (Xfce's login screen) just after logging in. I can sometimes get past this if I click the mouse constantly while moving it around (weird...) I tried installing fluxbox and it did the same thing when loaded. Any suggestions?

---

### Post by Wim Sturkenboom on 2006-11-14
> **Unisyst said:**
> Any suggestions?Yes:
post your hardware specs
post your /etc/X11/xorg.conf (sections device, monitor and screen)
check your /var/log/Xorg.log (don't have ?Ubuntu at hand here so the log might be somewhere else)

---

### Post by Unisyst on 2006-11-14
Pentium III 256 MB Ram Voodoo 3. (real junker but it was free :D)

xorg.conf and Xorg.log ain't gonna be easy to get.. It seems to be getting worse (crashing more often now, so I suspect a hardware issue possibly) I'll see what I can get, but I tried the ubuntu forums on it in firefox and it crashed, so Im not sure, might have to reinstall... =/

---

### Post by Unisyst on 2006-11-14
Aha got it. Yay for using my MP3 Player as a 'flash' drive.

---

### Post by Wim Sturkenboom on 2006-11-14
Don't see much wrong. Only tip might be to remove all sections that refer to the wacom tablet. But I doubt if it will help.

Sorry, but I can't be of further help.

---

### Post by Unisyst on 2006-11-15
I think it's a hardware issues as Kubuntu's desktop kept crashing before as well, also even on the install of Xubuntu it crashes the first time and then on the second try it's fine. I'm thinking it's the video card it's an archaic P.O.S. anyway. I can't seem to find my old Banshee Blaster either. Oh well I'll try what I can.

---

### Post by Unisyst on 2006-11-15
Yup! It's hardware for sure, Windows 2000's install BSODs. ](*,) 

Oh well maybe I'll find another free PC (I seem to be a magnet for them).

---

### Post by valavanisalex on 2006-12-25
I'm another Xubuntu newbie and I've had exactly the same problem on my dad's elderly PC.  He has a 3dfx Voodoo 3, and Xubuntu immediately crashes out of the desktop back to the login page.

I'm visiting my parents for a few days, so I had a quick play with their PC, somewhere between christmas presents and dinner and had a little success :grin: 

Here's what I found...

Firstly, I switched to text mode terminal, using ctrl+alt+F2 so I didn't have to deal with the wierd gdm login problems

Next, I logged into the text terminal and I edited the xorg config: 

**sudo pico /etc/X11/xorg.conf**

I added a line to the "Device" section for my 3dfx card to switch off hardware acceleration:

**Option "NoAccel" "true" #Removes hardware acceleration**

I saved and restarted the computer.  As if by magic, the desktop now works.  :-D 

We now know the problem is with the hardware acceleration with the 3dfx driver.

The next challenge is to enable hardware acceleration again!  Any suggestions?

---

### Post by Kapernicus on 2007-01-07
djsik,

You are a genius!!!!  I have been struggling with this all weekend and I finally started to believe that it was in fact my old timey video card.  Your trick fixed my issue as I was having the same problem while running the live CD.  However, since it was a live CD, I didn't have the luxury of restarting the machine.  For anyone else having this problem, here's what I did:

Logged in using the terminal

Edited the xorg.config file:

**sudo pico /etc/X11/xorg.conf**

I added a line to the "Device" section for my 3dfx card to switch off hardware acceleration:

**Option "NoAccel" "true" #Removes hardware acceleration**

Find the PID of the xserver via the following command:

**sudo ps -au**

Then, using the PID obtained from the ps command, kill the X server:

**sudo kill *[X server PID]***

Its a hack, but at least it works!  ;)

---

