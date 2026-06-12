---
title: "Gutsy 7.10 Black Screen"
date: 2007-10-24
forum: General Help
---

### Post by illuminaris on 2007-10-24
I've read a lot of posts about people who get black screens and start in low graphics mode, but none of them have been helpful and the good majority are people with variables that don't apply to me, so I am starting my own thread. I apologize to those who feel this is a waste of space, but I need help.

Everything was working fine on Fiesty and then I got the update for Gutsy from the automatic updater. When it finished, it suggested that I restart, so I did. After the restart, my screen went black after the initial orange loading bar. Instead of a log-in screen I got a black screen. My monitor would restart about 5 times and then it would offer to go into low graphics mode. That is what I have been running in for the past few days, and I am running in low graphics mode now.

I have tried numerous solutions, none of which have worked, including:
1. Downloading startupmanager and changing resolution to 1024x768
2. Installing several different forms of ATI drivers, none of which have helped
3. Reconfiguring my xserver-xorg 

I'm running an ATI Radeon 9800 Pro. I am almost certain this is a graphics problem. I can get to the text login screen by hitting ctrl+alt+f1 at the black screen, but from there I can not do startx, it just gives me errors.
I do not use Live-CD, nor am I using dual-boot with windows. I only have Linux installed, and only one version, Gutsy Gibbon 7.10.
My monitor is a SAMSUNG SyncMaster 955DF.

It has been able to detect both my specific monitor and my specific graphics card. At first my xorg.conf file was empty but I have since fixed that with one of the ATI driver installs I did.

Please help.
I am new to Linux, so please explain in basic terminology and step-by-step directions to make it easier for me and the other people who will read this thread.

Thanks.

---

### Post by illuminaris on 2007-10-24
bump

---

### Post by krebzepplin83 on 2007-10-24
bump...
im getting the same problem... but i dont get a option for low graphics blah blah...
and when i screen goes black my keyboard stops responding... i know this cause i cant even turn on numlock, caps lock, scroll lock.
please some one help us out lol... i will keep bumping:guitar:

---

### Post by krebzepplin83 on 2007-10-24
bump... i have to go do some laundry... bbl pm me we get a working solution please

---

### Post by drama1981 on 2007-10-24
try sudo dpkg-reconfigure xserver-xorg

be careful though i think its second to the last screen it asks for screen resolutions be absoultely sure only the resoultions that are supported by your monitor are selected.

you could also try an older version of xserver-xorg-ati  the recent version is seriously bugged many people are having various problems with it, strangely on a per user basis as opposed to the per card basis that we are used to.

---

### Post by illuminaris on 2007-10-25
My brother solved the problem!
You just have to go into your xorg.conf which you can do by using either one of these commands
```
sudo dpkg-reconfigure xserver-xorg
```

or

```
sudo gedit /etc/X11/xorg.conf
```

Once you're editing the xorg config, look for anything to do with screen resolutions. When you come to that section, delete or uncheck ANY lines that have to do with resolutions that are higher than your screen can handle. Don't delete the whole section, just delete that one line that will be in quotes.

This will solve the problem. Reboot and good luck!

Note: I fresh installed a brand new ATI fglrx driver before this, the newest one from ATI, so that may have helped as well, but it should work either way.

---

### Post by krebzepplin83 on 2007-10-25
i cant see that code!!!! lol

---

### Post by uprightnetizen on 2007-10-25
Hi, I had the exact same problem as krebzepplin83, my keyboard was unresponsive and I had to log in without xserver.  

I did:
```
sudo dpkg-reconfigure xserver-xorg
```

I just chose the default for just about all the options, Except when I got to the screen resolutions, I unchecked anything higher than 1024x768.  To un-check things, use the spacebar (not enter).  Then after restarting, xserver worked fine.  I noticed the new xorg.conf file left out a lot of things in the 'Device' section about my ATI Radeon 9600 card,  I think it was probably my card, and not the screen resolution causing problems... but I don't feel like experimenting right now.

---

### Post by mikeinwin on 2007-10-25
Got to xorg.conf - 1024x768 is the only defined screen size and is the correct recolution for my Toshiba Internal 1024x768 Panel.

Still boots to a black screen.

I can boot the 6.06 desktop CD no problem.

When I boot the 7.10 CD, I can start and choose "start or install" and then after some loading, the screen goes black.

I am closer to a solution and closer to the end of my rope.

---

### Post by antonio92 on 2007-10-26
You should check out this thread:
[http://ubuntuforums.org/showthread.php?t=580020]("http://ubuntuforums.org/showthread.php?t=580020")

I've got the same problem, I can boot the 6.10 Edgy Eft CD, but not 7.04 nor 7.10.

I have a Fujitsu Siemens Scaleo P computer with 512 MB RAM and an ATI Radeon X600 graphics card.

---

