---
title: "I HAD TO TOTALLY REINSTALL UBUNTU help?"
date: 2008-01-23
forum: General Help
---

### Post by adn258 on 2008-01-23
okay earlier and I won't make this mistake again I was messing with the SCREENS AND GRAPHICS part of ubuntu.  Anyway I changed a setting with the graphic card i like moved it away from the standard setting and then restarted my computer only to find out that it wouldn't boot past a certain screen it said something like running scrip /etc or something and it wouldn't move past there does anyone know why?  How to prevent this stuff in the future?

---

### Post by zivxx on 2008-01-23
When you say moved it away from the standard settings, could you give us a bit more information about what you did, like did you installed new driver, or did you went on system->administration->Restracted Devices Mangaer and enabled the option there(usually there is only one option), have you installed compiz and used it's screen effects? try to be more spesific cus i had many problems of this kind in the past and each one has it's own configuration

---

### Post by silviur on 2008-01-23
Next time you change Screen and Graphics settings, use Test first to ensure that te new settings will work.

---

### Post by Kingfield on 2008-01-23
You should have at least got to a terminal screen, and from the terminal you can change the graphics settings.

---

### Post by cdenley on 2008-01-23
I think on recent ubuntu releases, the last thing you see on the terminal is something about running /etc/rc.local, since this happens after the login prompt appears. If you press enter, the login prompt will be printed again. Or you could press ctrl+F2-6 to switch to a virtual terminal. All you had to do is login, then run "sudo dpkg-reconfigure xserver-xorg". This would have reconfigured /etc/X11/xorg.conf, fixing any changes you made which caused X to not start.

---

### Post by adn258 on 2008-01-23
> **cdenley said:**
> I think on recent ubuntu releases, the last thing you see on the terminal is something about running /etc/rc.local, since this happens after the login prompt appears. If you press enter, the login prompt will be printed again. Or you could press ctrl+F2-6 to switch to a virtual terminal. All you had to do is login, then run "sudo dpkg-reconfigure xserver-xorg". This would have reconfigured /etc/X11/xorg.conf, fixing any changes you made which caused X to not start.

okay thanks dude I will keep that in mind if it ever happens again I appreciate you guys helping

btw if anyone is curious I messed with the graphics card where it says vesa driver or whatever after I changed it I had this problem tell me if something like this happens how can I like backstep or fix the problems in recovery mode?

---

### Post by adn258 on 2008-01-23
> **adn258 said:**
> okay thanks dude I will keep that in mind if it ever happens again I appreciate you guys helping

btw if anyone is curious I messed with the graphics card where it says vesa driver or whatever after I changed it I had this problem tell me if something like this happens how can I like backstep or fix the problems in recovery mode?

read above for what happend

---

### Post by Battie on 2008-01-23
> **adn258 said:**
> okay thanks dude I will keep that in mind if it ever happens again I appreciate you guys helping

btw if anyone is curious I messed with the graphics card where it says vesa driver or whatever after I changed it I had this problem tell me if something like this happens how can I like backstep or fix the problems in recovery mode?

I assume you changed it to something like NVidia...

If you ever find yourself stuck without graphics and at a terminal (which can always be accessed by selecting Recovery Mode at the GRUB menu), edit your /etc/X11/xorg.conf file:

-Make a backup with 

```
cp /etc/X11/xorg.conf /etc/X11/xorg.old
```

-Use a text editor to make changes.  I use vi:

```
sudo vi /etc/X11/xorg.conf

```

-Scroll down until you find a Section "Device" with nvidia or ati listed as the driver.  Press "a" to append and change the driver to nv, the generic driver.

-Press esc to exit edit mode.

-Press :wq to save and quit.

-Restart, or just restart X.

I hope that addresses your issue!

---

