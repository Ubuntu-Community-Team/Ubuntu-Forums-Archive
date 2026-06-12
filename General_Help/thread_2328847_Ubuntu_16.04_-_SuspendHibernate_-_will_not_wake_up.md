---
title: "Ubuntu 16.04 - Suspend/Hibernate - will not wake up!"
date: 2016-06-24
forum: General Help
---

### Post by jay30 on 2016-06-24
I have recently installed version 16.04 (was previously on 14.04).  I am running on an HP desktop AMD64 (Athlon X2).  My machine goes into what I assume to be suspend or hibernate mode if away from the keyboard for a few mins (not sure how long - maybe 10).  The problem is, I am unable to wake it up.  The power light is still on (which maybe means it is in suspend as opposed to hibernate).  The only solution I have at the moment is to power down the machine and reboot.  This is silly - I can't keep restarting my pc this way everytime I come back to it after a few mins.  I have scoured the internet looking for possible solutions and have heard that others are having some issues but maybe mainly with laptops.  The one suggestion I did find was to upgrade the kernel (which sounded promising).  I upgraded to 4.4.8-040408-generic, however, this did not solve the problem.

What options do I have - can I somehow turn off the suspend from happening?  What about a fix from Ubuntu?  Any additional advice is greatly appreciated.  Thank you.

---

### Post by Irihapeti on 2016-06-25
Have a look at the settings in your power manager.

I'm not clear which desktop environment you're using, but I assume that similar settings will be available as in Xubuntu, which I use. I have suspend set to Never but I allow the screen to turn off after a set period of time.

---

### Post by jay30 on 2016-06-25
Within System Settings -> Power it is set to "Don't Suspend".  So not sure what the problem is.  I also just upgraded the kernel again to 4.5.  But still no resolution.

---

### Post by QDR06VV9 on 2016-06-25
There is also an app called caffeine [https://launchpad.net/ubuntu/xenial/+source/caffeine](https://launchpad.net/ubuntu/xenial/+source/caffeine)  < which will stop the display from blanking> (Going Black)

and also a few terminal commands to use for example
```
xset s 0 0
```
Or 
```
xset s off
```
Or disable energy star settings
```
xset -dpms
```
one of those should work.

---

### Post by jay30 on 2016-06-25
xset -dpms seems to have worked.  so my monitor stays on even after gone for a while.  will probably just physically turn the monitor on/off now I guess.

---

### Post by jay30 on 2016-07-01
Again the xset -dpms worked.  However, I believe if/when i reboot my machine I return to the old problem (because it has returned).  is there a way to have this setting stick permanently?  Thanks.

---

### Post by QDR06VV9 on 2016-07-02
Just add that to your start-up Applications in Settings.

---

### Post by gadaletas on 2016-10-24
After several researches (edit /var/lib/polkit-1/localauthority/ ... or edit /etc/polkit-1/localauthority/ ...), I can hibernate my Inspiron 531 AMD64, creating a Desktop Entry file as follows: 
[Desktop Entry]
Encoding = UTF-8
Version = 1.0
Type = Application
Terminal = true
Icon [en_US] = gnome-panel-launcher
Exec = sudo pm-hibernate
Name = Hibernate

---

