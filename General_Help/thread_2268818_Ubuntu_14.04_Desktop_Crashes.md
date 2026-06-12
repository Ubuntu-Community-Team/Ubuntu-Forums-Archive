---
title: "Ubuntu 14.04 Desktop Crashes"
date: 2015-03-11
forum: General Help
---

### Post by Tim_English on 2015-03-11
I just recently installed 14.04 on my Compaq Presario A900 and majority of the time everything works fine, althrough recently i have beem recieving crash notices on start up, i will look more into them and report back about it, but my main problem and reason for posting this, i am using google chrome i should add, but anytime i go on youtube and play a video the desktop crashes and i am forced to restart the computer using the tty1 terminal screen because the shortcut for the normal terminal wont work after it crashes, i should mention that by crashing i mean the side launcher dissappears, the top menu dissapears, and the top bar of all the windows with the minimize, maximize, and close buttons dissapear, i tried doing some searching and could not find a solution that works besides restarting the computer

---

### Post by v3.xx on 2015-03-11
According to the specs I found, your computer is limited to 2G of ram.  
[http://www.hp.com/ctg/Manual/c01295803.pdf](http://www.hp.com/ctg/Manual/c01295803.pdf)

How much ram are you running?  You could be pushing your processor and video to its limit.

Try installing another desktop environment to compare performance.  An easy one to install is Flashback.
```
sudo apt-get install gnome-session-flashback
```
Reboot and at the login screen click on the icon and choose Flashback (metacity).
My guess is you will see a performance boost.

---

### Post by Tim_English on 2015-03-11
The computer has 3gb of ram duel core 2ghz processor, and i will give that a try and report back how it works

EDIT: the Flashback Metacity options seems to work in the short test i did, the Flashback Compiz option crashed right away just like the unity desktop

---

### Post by v3.xx on 2015-03-11
Unity also runs compiz.

---

### Post by Tim_English on 2015-03-11
Yeah i did know that one of the other solutions i read about was that you can restore the desktop by re-enabling the unity and associated plugins, this did not work in my case

---

### Post by CantankRus on 2015-03-11
Try enabling hardware acceleration....
[http://www.webupd8.org/2014/01/enable-hardware-acceleration-in-chrome.html](http://www.webupd8.org/2014/01/enable-hardware-acceleration-in-chrome.html)

---

