---
title: "Unwanted restarts"
date: 2016-04-02
forum: General Help
---

### Post by Horsepower on 2016-04-02
About 6 months ago, on desktop 15, when I select shut down the computer would always restart. I thought an update may fix it so I waited, but it didn't. Today, frustrated, I wiped the drive and installed 16 and the same thing happens. I am totally at a loss on this one.

---

### Post by ajgreeny on 2016-04-02
Tell us more about your hardware; sudden restarts like that could be the result of overheating, or a bad memory module, the second of which you could check by running MemTest86+ from the grub menu.

---

### Post by Horsepower on 2016-04-02
Gigabyte GA X79 UD3 with 16 gigs of ram. Sorry to not be explanatory. It started after an update about on 15 about 6 months ago, and I run windows on a separate drive with no problems. It doesn't just restart without me trying to shut it down. When I shut Ubuntu down, I select "shut down" and then the shut down button instead of restart, but it restarts anyway. I actually have to unplug it in between. Before that update 6 months ago on 15 there was no problem at all. Thank you.

---

### Post by Horsepower on 2016-04-05
Bump?

---

### Post by pei-ollllo on 2016-04-05
Sorry, I have no definitive answer.   However, I can confirm your symptoms. 

  I also started having restarts occur after choosing [Shut Down].  It was also a Gigabyte board, 88GMA and it was Ubuntu 14.04 at the time. Oddly enough, I noticed a pattern that it happened regularly from the panel button but I never saw it happen once from the Cairo Dock power icon.  Could have been coincidence or it could have been a clue beyond my ability to process.

I can tell you that it went away after a complete fresh install of 15.10 (done for other reasons) but that is an extreme fix for your case.

---

### Post by ajgreeny on 2016-04-06
To shutdown using a terminal command that does not need to be run as root try
```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```
If that works as it should, you could create a **shutdown.desktop** file, ie a shortcut to that command, or run it as a script in order to shutdown and halt as it should.

---

### Post by Horsepower on 2016-04-09
That doesn't work, something about not recognizing HAL

---

### Post by ajgreeny on 2016-04-11
Ah! I forgot about hal which I have installed from a ppa repository for another reason. Hal is now deprecated, I believe, so we should look for alternative solutions.

I will do more searching later when on a "proper" OS, not an android tablet.

---

### Post by ajgreeny on 2016-04-11
Have a look at this long thread with a few possible options to get a machine to shutdown properly; not quite the same problem as yours in detail, but worth a read through and try-out of some of these suggestions, I think.
[http://ubuntuforums.org/showthread.php?t=2217602](http://ubuntuforums.org/showthread.php?t=2217602)

---

### Post by Horsepower on 2016-06-03
I have posted for months about this problem and I am TIRED of it. No matter what I select the computer ALWAYS restarts. There are NUMEROUS posts about this.

---

### Post by oldos2er on 2016-06-03
Threads merged.

Have you tried the suggestions in posts #16 and #17 [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1346269")?

---

### Post by Horsepower on 2016-06-03
Yes, I tried every suggestion. I have a script on my desktop to shut it down and that doesn't work either. This should be simple but I STILL have to pull the power cord after selecting shutdown, and I cannot even begin to explain my frustration.
It's a Gigabyte GA X79 UD3. I have no internal hard drive, I boot to hard drives in a front loading rack, all other Oses work fine.

---

### Post by ventrical on 2016-06-03
> **Horsepower said:**
> Yes, I tried every suggestion. I have a script on my desktop to shut it down and that doesn't work either. This should be simple but I STILL have to pull the power cord after selecting shutdown, and I cannot even begin to explain my frustration.
It's a Gigabyte GA X79 UD3. I have no internal hard drive, I boot to hard drives in a front loading rack, all other Oses work fine.

I have had this problem multiple times on various installs and PCs. Locks up my KVM .. have to pull cords and then plug them back in. With or without KVM it has been a problem on different machines. 

 I have one question: Did you build your own PC?

 I have built all of my own PCs with the exception of a few laptops and tablets. The only solution I found to my problems was to do:
1. Check settings in BIOS (most obovious place of troubles)
2. A fresh install.
3. Change the power supply.!

 I am assuming there is a setting in BIOS that is the problem  but usually a fresh install is the best way to  get rid of this horrible bug.

Other methods I use involve removing the memory sticks and then re-installing them. What is your graphical card because  usually nVidia machines seem to be most often affected.



Regards..

---

### Post by Horsepower on 2016-06-03
Thank you, but on April 6 I wiped the drive and clean installed Ubuntu 16. Ubuntu 15 had the SAME problem, that started with an update in October 2015. Before that, Ubuntu 15 shut down fine.

---

### Post by Horsepower on 2016-06-27
You would think after all of the time, one of the updates would fix this problem.

---

### Post by Horsepower on 2016-07-29
You would think SOMEONE else would have this same problem!

---

### Post by Horsepower on 2016-08-13
Well, I was so excited a week to 10 days ago because an update happened and the machine would shut down. TODAY another update happened and it is BACK to the old restart every time it shuts down. Ubuntu back on the shelf for a month. DAMN!

---

### Post by Horsepower on 2016-08-13
OK SHAME on ME I retraced my steps from a week ago and remembered I had my external drive disconnected when it shut down correctly. It is a lot easier to unplug the external than it is to pull the power cord in between. I would still like to figure out what is causing this, but an easier workaround is disconnecting the 3TD USB3 MyBook first.

---

