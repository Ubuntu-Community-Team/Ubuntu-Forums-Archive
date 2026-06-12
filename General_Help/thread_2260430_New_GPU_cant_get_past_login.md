---
title: "New GPU cant get past login"
date: 2015-01-11
forum: General Help
---

### Post by Adam_Alvis on 2015-01-11
Hi guys,

I recently installed a new GPU (gtx 970) and now Ubuntu won't go farther than the login screen.  If I type in my password it accepts it then freezes at just my blank wallpaper.  I can still move my mouse around, but the desktop is never loaded.  I use my install exclusively for development and all my work is backed up to bitbucket, so I went ahead and reinstalled ubuntu.  I was able to get to my desktop after installation, but only one of my monitors was working.  So I downloaded/installed the latest Nvidia driver and restarted my machine.  I get back to the login screen and same issue.  I can get past login, but the desktop never loads.

Is anyone else having issues with the gtx 970?  Any suggestions/help is greatly appreciated.  Having to work at home on my Windows install makes me want to throw things.

Thanks in advance!

Adam

---

### Post by phidia on 2015-01-11
I'm thinking that maybe something was left behind when you reinstalled but maybe not. Have you checked [logfiles]("https://help.ubuntu.com/community/LinuxLogFiles#Daemon_Log") to see if there was anything in them that would point out the problem?

---

### Post by Adam_Alvis on 2015-01-12
Is there a way to check without logging in?

---

### Post by Adam_Alvis on 2015-01-12
Finally got it working. I completely removed the Nvidia driver and was able to log in.  I reinstalled and looks like everything is good now.

---

### Post by efflandt on 2015-01-12
Note that you may need a newer version than the initial nvidia-current, which even in 14.04 is a rather old 304 version that does not support the new Maxwell nvidia chips on GTX 750, 970, 980 series. Although, maybe if nvidia-current gets updated it can find something that works because somehow my GTX 750 Ti works on an emergency 64-bit Ubuntu 12.04 version I still have on SSD which I think still has a 304 version of nvidia drivers.

Although, my new GTX 750 Ti worked in 14.04 live/install DVD, when I booted the installed system, I had no gui at all (not even login screen) and could not log into text consoles at all, which would show motd and immediately dump me back to login prompt. Installing nvidia-current got me the login screen, but no X. I forget if it was dmesg or something in /var/log that said the nvidia 304 driver did not support my card. So I purged nvidia-current and installed nvidia-331 and then everything worked. Although, I wanted to play around with overclocking ( [http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item](http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item) ), so I added xorg-edgers ppa and updated to nvidia-346 (currently 346.22). Note that even Nvidia Experience in Win7 did not recognize the capabilities of my card for optimizing games until I updated its drivers from a 344 version to 347.

I was considering trying a GTX 970 which may have also require PSU upgrade or building a PC for it, but have not built a PC from scratch yet. So instead I swapped my GTX 550 Ti to GTX 750 Ti which reduced power use of my PC (Kill A Watt meter on AC input) from 200+ watts to 150+ watts max (little more than 145w or 970 alone) and reduced idle power from 75w to 50w.

---

