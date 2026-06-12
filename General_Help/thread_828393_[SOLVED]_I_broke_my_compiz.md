---
title: "[SOLVED] I broke my compiz"
date: 2008-06-13
forum: General Help
---

### Post by Novega on 2008-06-13
It worked before but I decided to restart my computer today and I've lost AWN & cant enable desktop effects... I've never had any real problems like this before.

I tried ```
 novega@computer1:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0622 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

Could anyone provide me with a starting point to troubleshoot this problem?

---

### Post by bren21 on 2008-06-13
The same exact thing happened to me, with the same message. Did you happen to install the latest x-server xorg updates before you restarted? I'm thinking that might have done it to mine.

---

### Post by Lacrimstein on 2008-06-13
Yup. Same with me. The X update is most likely causing the problem

---

### Post by Novega on 2008-06-13
I'm not sure what updates I had, the system didn't call for a restart...I just decided to restart since my computer had been on non stop for 3 days.

---

### Post by emid on 2008-06-13
I have the same problem.  I rebooted and now it doesn't work.  The X update is the only thing I can think of as well.

---

### Post by bren21 on 2008-06-13
Any way to uninstall the update?

---

### Post by Happy_Man on 2008-06-13
This is my issue as well, anyone know a solution?

I mean, I had to move to Openbox (granted, I really really love Openbox now, and am never going back to GNOME ever again ever, but still)

---

### Post by quoderat on 2008-06-13
Same problem here. Downgrading Xorg core did not fix it. Not sure what to try now. Was this not tested beforehand?

---

### Post by Necreia on 2008-06-13
Yep, same story here.  My visual effects are toasted after the update.

---

### Post by Necreia on 2008-06-13
I fixed it!

All I did was re-install my video driver, and it all came back.  I saw something about a 'symbolic link' during the driver reinstall that was different from the usual, but none-the-less it works now.

8800gt
x64

---

### Post by Novega on 2008-06-13
well forget this, I'm going back to windows!!   j/k! You guys can't get rid of me that easily.

Nice to see I'm not the only one. I was kinda worried that I did something wrong. I really don't have any ideas of what to do. I wonder if```
 sudo dpkg-reconfigure xserver-xorg
```  or ```
sudo nano /etc/X11/xorg.conf 
``` would do anything?

I'd try it myself but I'm a noob and I'd probably just mess it up.

I'm running 64 bit...wonder if it's a problem specific to amd_64?

Not Having AWN is killin me :(

---

### Post by quoderat on 2008-06-13
That worked! Thanks. I just re-loaded the Nvidia driver, and it was cool and the gang.

---

### Post by Lacrimstein on 2008-06-13
Yay! Reinstalling the graphics driver fixes it. Maybe its just me, but compiz seems to be running even faster now :KS

---

### Post by Novega on 2008-06-13
Yeppers, worked for me :)

I got the same error about libglx.so not being a symbolic link. But it's working so I'm gonna go ahead and mark this one "SOLVED"  

Good Job!

---

### Post by bren21 on 2008-06-13
Sweet, I'll have to go ahead and do that.

---

### Post by nhasian on 2008-06-14
yep i also wanted to say i encountered this problem as well.  simply reinstalling my video driver did indeed resolve the issue for me.  I'll bet a lot of people are affected by this last update.  we should put some tags like "Desktop Effects could not be enabled" or something about "visual effects" since that was what i was originally searching for.  I figured compiz was working fine since but was unable to run because the visual effects under the appearance preferences was stuck on none and would not allow me to set it to normal or extra.

---

### Post by bren21 on 2008-06-14
Reinstalling the driver worked, but compiz doesn't load on start up. Anyone know a fix for this?

---

### Post by Forlong on 2008-06-15
How do you start Compiz?

---

### Post by techstop on 2008-06-15
I'll add my voice to the chorus here. 

Running a 9600GT, I also reinstalled the NVidia driver to fix the non-working compiz. I also got the error about the symlink someone posted earlier.

---

### Post by Bryan on 2008-06-15
I had the exact same problem as everyone else.  Reinstalling the driver worked fine for me too.  

I just made sure I didn't overwrite the xorg.conf file during the installion as the current one was working fine before the reboot.

---

