---
title: "Unable to login after kernel update today"
date: 2016-07-14
forum: General Help
---

### Post by xeddog on 2016-07-14
I have an Ubuntu 15.10 machine that has been running fine for Months.  This morning I ran the updates and the only thing I saw was a kernel update.  There could have been something else, but the kernel is all I saw.  The update seemed to run fine, but upon reboot I am presented with the login screen.  I should note here that this is a single user machine into which I am auto logged in.  Anyway, on this login screen I see three users named "Comment", one "Samba Guest", and one "Guest".  Samba Guest, and Guest are supposed to be disabled, and my user id is NOT one of the selections.  Of the three "Comment" users, two have the default Ubuntu purple background, and one has the desktop image from my userid.  However, NONE of them will accept my password, meaning they all report it as invalid.

I can do a Ctrl-Alt-F1 and get a terminal window that I can use my userid and password to login with. but I just don't know what to do from there.  I am using a different machine to enter this post and so cannot get a screenshot or log files from the other one.

Any help is appreciated, including help on where to look to find out what has gone haywire.

And one last question before I go, is there any way to upgrade the machine to 16.04 from the terminal command line?  I have been considering upgrading for a couple of weeks now so this might be a good time if I can do it.

Thanks,

Wayne

---

### Post by DuckHook on 2016-07-14
Sorry to hear about the hiccup, xeddog.

Before attempting a command-line version upgrade, please make sure you data is backed up. I am assuming that you have quite a bit of data needing backup if you've been running 15.10 these past few months. If not backed up, that is your very first order of business.

If data is safe and demonstrably restoreable from backup, then I recommend a complete install of 16.04 from scratch. What you are asking about is a network upgrade and they are finicky at the best of times. It is no time to try this when you already have a broken login currently. However, if you wish to go that route anyway, then simply:```
sudo do-release-upgrade
```

We can try a few things to bring 15.10 back, but from what you have stated, you intend to move to 16.04 anyway. This is a very wise move since 15.10 has reached end-of-life. The only reason to monkey with it at this point is to enable a data backup, but this can also be done through the command line.

---

### Post by grahammechanical on 2016-07-15
You need to get a Grub boot menu. If Ubuntu is the only OS then you will not see a boot menu unless you press Shift as the motherboard goes from its Power On Startup Tests (POST) to handing over to Grub.   At the Grub boot menu select Advanced options for Ubuntu and in the sub-menu you should see earlier kernels listed. Try one of those.  Regards.

---

### Post by xeddog on 2016-07-15
OK, I got this figured out and fixed.  The problem was video drivers.  As I was googling around trying to find a resolution, I saw where some people had a similar thing happen, and one of the things suggested was to show which video drivers were installed using "sudo lshw -c video".  So when I was at the login window I did ctrl-alt-f1 to get a terminal window and logged in.  When I issued the command, there was no driver listed.  After some more digging around, I did a "sudo apt-get remove nvidia-352" to remove the nvidia driver, and then rebooted.  When the machine came back up, it logged me in the way it used to, but there were obviously still problems.  Only one of my dual monitor setup was working, and the resolution sucked.    

From there, since I had a gui, I launched the additional drivers program so I could try to install the drivers again.  It showed that I was using the Nouveau driver which I expected.  There were 4 other drivers listed that I could select from.  Two were the nVidia 340.96 drivers and two were nVidia 352.63 drivers.  The driver I was using before was the one labelled "NVIDIA binary driver - version 352.63 from nvidia-352 (proprietary[COLOR="#FF0000"], tested[/COLOR])", but when I attempted to install it, the install process hung when the progress bar was around 80-85% completed, and the install would not complete.  A reboot got me back to the login screen and I could not get logged in from there.  

So ctrl-alt-f1 again to get the terminal window and remove nvidia-352 again, then reboot.  I tried to install the nVidia driver again, and it failed again, so I removed it again.  After a reboot, I tried to install the other 352.63 driver labelled as "NVIDIA binary driver - version 352.63 from nvidia-352[COLOR="#FF0000"]-updates[/COLOR] (proprietary)".  This one DID install and I was back in business.  I did lose a few custom settings and tweaks, but that was minor stuff and easily corrected.

To respond to your suggestions - 

DuckHook - There are a couple of minor things that I would need to back up, but if I lost them it wouldn't be too traumatic,  I have three hard drives in my machine.  One just for the OS, a separate internal disk drive containing /home, and an external USB 3.0 disk for data and weekly backups.  So if my linux drive were to crash it's not a HUGE deal, just a big deal.  :-)

Grahammechanical - One of the things I did was to boot using the previous kernel.  There were a couple of strange things that happened there, like like loading a different desktop, but it did come up.  However, before I found out what the problem was I did a really dumb (REALLY dumb) thing and ran a "sudo apt-get autoclean" which removed all of the previous kernels.  dumbdumbdumbdumb.](*,) #-o


Wayne

---

### Post by DuckHook on 2016-07-16
Good to hear you're back in business. Just one word of caution: if you go through with plan to network upgrade, make sure you nuke the nVidia driver and go back to nouveau. You can always reinstall the nVidia after the upgrade. The closer you are to pristine state, the higher your chances for a successful network version upgrade.

---

### Post by xeddog on 2016-07-16
Well, your advice is sound, but too late.  :P  After tweaking things and rebooting a few times just to make sure that everything was ok, I went ahead and upgraded.  To do the upgrade, I just closed all running applications, opened a terminal window and ran "sudo do-release-upgrade" in the terminal.  Everything was going great for the first 15-20 minutes and then it all turned to manure.  It took several "sudo apt-get update", "sudo apt-get upgrade", and "sudo apt-get dist-upgrade" commands with a couple of "sudo dpkg --configure -a" and "sudo apt-get autoremove" commands thrown in, but eventually I got to the point where there was only two packages that did not install because they were held back and they had to do with jpeg handling.  After all that, I rebooted and everything seems to be working.  But the point of this reply is that the install process removed the nvidia 352 driver and installed the 361 driver automagically.

Wayne

---

### Post by DuckHook on 2016-07-16
\\:D/

So long as it all works out in the end, everything is good.

Happy Ubuntuing!

---

