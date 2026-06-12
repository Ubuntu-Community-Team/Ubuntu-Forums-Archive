---
title: "Sound Issues in Flash"
date: 2008-06-08
forum: General Help
---

### Post by edxmonkey on 2008-06-08
I may be posting this in the wrong area - if so, I apologize.

I've installed flash player for Firefox, however, I'm not getting any audio with it. Also, when trying to view Youtube videos, the video player doesn't load...  

Given, I'm new to Ubuntu and I'm sure it's user error - though from what I gather from various websites, I'm not the only one having this problem.

I've tried installing the lib flash support and whatnot - and an Ubuntu update even installed it, though I'm still not getting any audio.

Again, I apologize if this is in the wrong area - but any and all help would be appreciated. Thanks!

---

### Post by ibuclaw on 2008-06-08
There is a very useful guide on streaming in Ubuntu found [here]("http://ubuntuforums.org/showthread.php?t=766683").

That should get you off your feet.

Regards
Iain

---

### Post by edxmonkey on 2008-06-08
Thank you.

However, my problem still is not solved. I read and followed all it told me, however, I still cannot hear audio in flash, play music, or see the Youtube Video Player...

Also, everytime I enter a command in the Terminal I have to use 'sudo dpkg --configure -a' before anything, as it tells me that it's interrupted.

After that when trying to Purge then Install Adobe Flash I get the following message 

$ sudo apt-get purge flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
E: Couldn't find package nspluginwrapper

However, I know I've installed the plugin...

---

### Post by ibuclaw on 2008-06-08
Not to worry.
Try this instead (removed the non-existant package)
```
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

Regards
Iain

---

### Post by edxmonkey on 2008-06-08
Again, thank you for the assistance...

When I enter that command I get this as a final line:

dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.

I've gotten that more than once right before it jumps to a package configuration. 

Again I apologize for knowing -nothing- about Ubuntu... However, using it is the only way I'll learn. I'm just...a bit frustrated that I'm without sound.

---

### Post by wolfen69 on 2008-06-08
did you check your software sources first? go to system>admin>software sources and make sure everything is checked off.

---

### Post by edxmonkey on 2008-06-08
Yes, I did - all are checked except for "Source Code" which automatically checks the CD bit - then if I try to reload that, I get an error.

After unchecking it and reloading I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by schmy on 2008-06-09
I was having the same issue: i.e., sounds were working everywhere except Flash. I tried the uninstall-reinstall routine a number of times to no effect.

So I instead set a web-clip playing and moved my speaker plug from port to port until I found where Flash was outputting to.

I then checked my sound settings under System->Preferences->Control Centre and found all the settings were on "Autodetect". I left the speaker plug where it was and, using the "Test" button under the sound settings, manually configure all other outputs to the same port.

This worked for me; let me (and perhaps others) know if it works for you.

---

### Post by edxmonkey on 2008-06-09
Thank you for the suggestion - however, I'm on a laptop and I don't use any auxiliary speakers. ^^;

---

### Post by schmy on 2008-06-12
I'll be quiet if these are totally redundant questions:
- What audio options do appear in the settings?
- Wouldn't there still be "Auto-detect", "In-built speakers" and "Headphone port" (or equivalents)?

I'm just exhausting that possibility so that I can go to sleep knowing I'm wrong, rather than lying awake wondering, "should I have said something?"

---

