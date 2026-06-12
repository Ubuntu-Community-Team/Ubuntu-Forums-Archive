---
title: "Shut-down/Halt/Reboot Problem on a ThinkPad T61"
date: 2008-04-23
forum: General Help
---

### Post by lunatico on 2008-04-23
I am experiencing a weird problem on my T61 almost every time y want to shutdown or reboot my computer. I will try to explain in detail the shut-down process.
I have Ubuntu 7.10 kernel 2.6.22-14-generic. On a fresh installation of Ubuntu the problem will not occur, so some where along the way I did something...
I will select the normal Shut Down option and the shut-down process will start as it should. I have the quiet option off in the grub menu.lst so I see what's going on during boot up and shut down. The last two lines there will say:

Unmount local filesystems
Will now halt

Then it will be there like for 10 seconds and then it goes to a black screen, with a blinking cursor in the top left of the screen and nothing else will happen after.
From there I can do ctrl+alt+F1 and go to tty1 and it shows the login screen but I can't type anything. The other terminals (tty2, tty3, tty4, tty5 and tty6) are not accessible. But I can also go back to tty7 (ctrl+alt+F7) and see the last output from the shut-down process which is as follows:

* Starting anac(h)ronistic cron anacron
* Stopping GNOME Display Manager... 
* Stopping Avahi nDNS/DNS-SD Daemon avahi-daemon
* Stopping DHCP D-Bus daemon dhcdbd
* Stopping ConsoleKit daemon console-kit-daemon
* Stopping disk temperature monitoring daemon hddtemp
Stopping Network Traffic Monitorin Programs: tleds
* Stopping ThinkPad fan control daemon tpfand
Stopping wicd daemon...
* Saving the system clock
* Shutting down ALSA...
* Unmounting any overflow tmpfs from /tmp...
802.1x supplicant: disabled, see /etc/default/xsupplicant
* Terminating all remaining processes...
* Sending all processes the KILL signal...
* Unmounting temporary filesystems...
* Deactivating swap...
* Unmounting local filesystems...
* Will now halt

And that's it, from there nothing else can be done other than switching between tty1 and tty7. I will have to hold down the power button to shut down the computer or I can also do ctrl+alt+del which will display System Rebooting and just hang or something the reboot works.

I have checked the system logs but I don't think I found anything relevant. Or maybe I need to look at a different place.
Any ideas? Any help will be appreciated.

---

### Post by ryanhaigh on 2008-04-23
I don't know if it is the same issue causing this but on one of my older SMP machines I would have to press the power button to shut it down otherwise it would just sit at this screen as you are experiencing. The solution was to force the loading of the apm module which enabled the computer to shutdown properly. Not sure if this will help as your computer is far more modern, but it may still be related to apm/acpi issues.

---

### Post by lunatico on 2008-04-24
Well, let me stress that on a fresh installation the problem will not happen. It could still be something related to ACPI, the problem is that I don't know where to look or what to check that will point me to an answer.

---

### Post by ire on 2008-04-24
> **lunatico said:**
> Well, let me stress that on a fresh installation the problem will not happen. It could still be something related to ACPI, the problem is that I don't know where to look or what to check that will point me to an answer.

What graphics card is in your T61 - Intel, ATI, or Nvidia?

---

### Post by lunatico on 2008-04-25
I have the Intel graphics card. and the Wifi is the Atheros one. Thanks.

---

### Post by SteveONCSU on 2009-08-12
I'm having the exact same issue only with Ubuntu 9.04, kernel 2.6.28-14.  I thought this would be fixed by now.  I've got a Thinkpad T500, same family as the T61.

Any ideas anybody?

---

### Post by SteveONCSU on 2009-08-17
I've got ATI graphics (tons of fun I know).  I've seen power settings for this as well.  Could this be the problem??

---

### Post by azredwing on 2009-09-03
I got the same problem with my T61: I shut down and it hangs at a blank screen blinking the _ character.

Sometimes instead of _ I see @^, no blinking...

---

### Post by azredwing on 2009-09-04
Got some news about this. Check out [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/353303](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/353303)

> 
In fact if I disconnect the wireless before rebooting or halting I do not have the problem!


Upon disconnecting from my wifi and attempting to shut down, I can shut down successfully.

Interestingly, the prescribed solution, 

> 
Care to try installing the linux-backports-modules-jaunty package to see if it helps. It contains an updated compat-wireless stack. Please let us know your results. Thanks.


works for the user who opened this bug, but not for me. 

I will continue investigating. For now, I did iwconfig wlan0 essid off and now I can't get it back on...

---

### Post by SteveONCSU on 2009-09-04
I haven't had this problem in a while. I did update my wireless drivers with the compat-wireless pack....

---

