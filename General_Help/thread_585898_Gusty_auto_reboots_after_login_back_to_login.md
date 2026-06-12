---
title: "Gusty auto reboots after login back to login"
date: 2007-10-21
forum: General Help
---

### Post by desktop on 2007-10-21
I updated my 7.04 ubuntu box to 7.10 this morning. The update went ok but after it rebooted everytime I entered my username and password it would hang for a bit then reboot back to the login screen. I launched a safe gnome session and logged in just fine. My Dual monitor set up however was not working (desktop is mirrored on both screens). So I tinkered with it throughout the day and messed things up with my xorg.conf file so Now I am back to square 1 , the Xorg.conf has been restored to a good backup. and I can't log in without going into safe gnome. I am running a ATI radeon 9800 video card and had my desktop set to bigdesktop dual monitors prior to the upgrade. The bigdesktop appears to be working right up to the point of logging in (both montiors show background color but login screen is only on primary display). Any help or ideas on this would be great.

Desktop

---

### Post by desktop on 2007-10-22
Bump

---

### Post by NFITC1 on 2007-10-23
I'm having the exact same problem. I can get into any of the safe modes or recovery modes (which nothing works under, it's just good for editing conf files and/or installing/uninstalling packages) then the lappy reboots before I get a chance to see the errors on the screen. What is the log file for shutdown? That's the only thing I can think might have relevant info.
Just in case, is dmesg the only boot log? I found one of the "errors" that I got that made it sound like it couldn't initialize my processor. I'll be able to give the exact error in a few hours since I'm not at home right now. I looked at the Xorg log and there are a few (EE)s there too, but I can't tell if that's what's causing any of this or not. Help us plz!  D:

---

### Post by NFITC1 on 2007-10-23
I got it to work (more or less) after installing the 8.42.3 ati drivers. This wasn't easy as there is an issue with installing this package into Ubuntu. If you search the forums you'll find it.
I'm not getting direct rendering to work, but at least I'm not in safe mode anymore.

---

### Post by desktop on 2007-10-23
I used envy to install the older ati driver and I am getting everything to work in safe gnome but still can't log in normally. I am goin to try the new ati driver.

Desktop

---

### Post by desktop on 2007-10-23
Ok!!!
I installed the new ATI Driver v8.42.3 and it is working fine in safe gnome but I still can't log in normaly. Grrrrr. I think the problem is with a script that is trying to run after the login screen but I can't figure it out. Man I need help with this, I wish the Maytag repairman new linux :lolflag:

Any advice on how to trouble shoot this further would be appreciated.

Desktop.

---

### Post by NFITC1 on 2007-10-25
```
sudo apt-get remove xserver-xgl
```

This is what finally did it for me. Before I did this Gutsy was defaulting to the xgl. After I got rid of it I only had one display and it had direct rendering enabled.

---

