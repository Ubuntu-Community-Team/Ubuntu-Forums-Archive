---
title: "My Ubuntu Problems"
date: 2008-06-29
forum: General Help
---

### Post by rossjman1 on 2008-06-29
I have a couple problems with my Ubuntu installation. Any help is appreciated.
1) I'm trying to get my dual monitor setup working. I have ATI Catalyst Control Center installed. I can enable my second monitor and extend my desktop (the option is called "big desktop" in ATI CCC). However when I logout, restart, or restart X, my second monitor displays the exact same thing as my primary monitor (the option is called "clone desktop" in ATI CCC).
2) I just installed and configured ThinkFinger (fingerprint reader software for ThinkPad laptops), and now whenever I swipe my finger to log into gnome, nm-applet requests a password (nm-applet is required for my wireless internet to work). Is there any way to stop nm-applet from requesting a password?
3) This is a minor problem with Amarok, my album art gets jumbled on some songs. [http://img78.imageshack.us/img78/8232/screenshotamarokirunthivj5.png](http://img78.imageshack.us/img78/8232/screenshotamarokirunthivj5.png)

---

### Post by fedex1993 on 2008-06-29
um trying running ati catalyst control center with a sudo command and also can i see a screenshot of the catalyst control center never seen it before and there might be a certian button your not pressing

---

### Post by rossjman1 on 2008-06-29
I also tried it from the command line: sudo aticonfig --dtop=horizontal with the same results, so it's not that I'm not running CCC as root. I would also like to add that I have to reset my monitor settings after playing a full screen video game (such as wolfenstein: enemy territory). Here's the screen shots:

[IMG]http://img73.imageshack.us/img73/3889/screenshotcatalystcontrob7.png[/IMG]
[IMG]http://img339.imageshack.us/img339/9552/screenshotcatalystcontrio6.png[/IMG]

---

### Post by rossjman1 on 2008-06-29
Bump!

---

### Post by rossjman1 on 2008-06-30
I don't mean to be rude, but every thread I make seems to get 0 responses. It's a little disheartening to know that if I have a problem with Ubuntu, it's about 10x harder to find a solution than it is in Windows or Mac.

---

### Post by rossjman1 on 2008-06-30
come on...

---

### Post by rossjman1 on 2008-06-30
I'm starting to get pissed.

---

### Post by hurtstotalktoyou on 2008-06-30
First of all, please don't get pissed.  Nobody is guaranteed to have his or her problem solved by the community.  You may have to be the one to figure out the solution so that others benefit, rather than you benefiting from others.

That said, it sounds like what you need to do is figure out some way to save your settings to the xorg.conf file.  In nvidia-settings you do this by clicking the cryptic "save to X configuration file" button.  The ATI tool may have a similar button.  If it doesn't, browse the xorg.conf file in gedit (sudo gedit /etc/X11/xorg.conf) and see if you can figure out if you can change it manually.  Be careful, though, because if you **** up your xorg.conf file, you won't be able to boot into a GUI until you fix it (which I've never actually done, but which I'm pretty sure is a major pain in the ***).

---

### Post by rossjman1 on 2008-06-30
There is no save configuration button. I guess I will just have to change it everytime I log in, until ATI releases a newer version.

I have another problem though. I use Amarok to play music, and it works great. However, if I were to open a program that emits sound, then Amarok will freeze. WTF! I tried installing the amarok-engines package in hopes of using the gstreamer engine (instead of xine), but xine is the only one avail. I am totally opposed to using Exaile. Also, once Amarok freezes, it will not open unless I log out and log back in.

---

### Post by soccerboy on 2008-06-30
what DE do you use?  You could try Rhythmbox or Songbird.  I have never tried Amarok myself so I can't help there.

---

### Post by rossjman1 on 2008-06-30
Should I try to install this package? [http://packages.debian.org/search?keywords=amarok-gstreamer](http://packages.debian.org/search?keywords=amarok-gstreamer)
I don't know why Ubuntu doesn't have this package...

---

### Post by soccerboy on 2008-06-30
that is a pretty old package so gstreamer support from amarok may have been dropped.

---

### Post by VMC on 2008-06-30
I don't know anything about this video card, but is this how you installed it. It's for a previous ubuntu version:
[http://www.phoronix.com/forums/showthread.php?t=7193](http://www.phoronix.com/forums/showthread.php?t=7193)

---

### Post by rossjman1 on 2008-06-30
I installed my Ubuntu installation from the 8.04 live cd, and my card was autodetected (for the first time in Linux history!), all I had to do was enable it in the Hardware Drivers window.

On the bright side, I fixed my Amarok issue, by changing the output plugin from autodetect to alsa. So the only issue remaining is #2: *I just installed and configured ThinkFinger (fingerprint reader software for ThinkPad laptops), and now whenever I swipe my finger to log into gnome, nm-applet requests a password (nm-applet is required for my wireless internet to work). Is there any way to stop nm-applet from requesting a password?*

---

### Post by soccerboy on 2008-06-30
> **rossjman1 said:**
> I installed my Ubuntu installation from the 8.04 live cd, and my card was autodetected (for the first time in Linux history!), all I had to do was enable it in the Hardware Drivers window.

On the bright side, I fixed my Amarok issue, by changing the output plugin from autodetect to alsa. So the only issue remaining is #2: *I just installed and configured ThinkFinger (fingerprint reader software for ThinkPad laptops), and now whenever I swipe my finger to log into gnome, nm-applet requests a password (nm-applet is required for my wireless internet to work). Is there any way to stop nm-applet from requesting a password?*

Is your login password and your keychain password the same?

---

### Post by rossjman1 on 2008-06-30
How do I completely disable this keychain? I assume it's the same...

---

### Post by VMC on 2008-06-30
You mentioned about saving you configuration.

 Have you looked at "System-Preferences-Sessions", Session Options, and Remember Currently Running Applications

---

### Post by soccerboy on 2008-06-30
> **rossjman1 said:**
> How do I completely disable this keychain? I assume it's the same...

I don't know how to safely disable the keychain. There are many applications that depend on storing passwords, WEP keys, WPA keys etc. in pam (keychain)

---

### Post by rossjman1 on 2008-06-30
No, but that gave me an idea, to add the command to enable dual screen to my startup programs. I'll let you guys know if it worked in a bit.

It didn't work...

---

