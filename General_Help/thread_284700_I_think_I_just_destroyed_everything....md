---
title: "I think I just destroyed everything..."
date: 2006-10-26
forum: General Help
---

### Post by bg1256 on 2006-10-26
I just installed Dapper on my desktop today, after running it on my notebook for about two months.

I had everything working. My nvidia card, good resolution, etc., etc.

However, when I was following the Howto located [here]("http://www.ubuntuforums.org/showthread.php?t=263840&highlight=howto+nvidia+xgl"), crazy stuff happened.

About halfway through the guide, it tells you to reboot your system.  So I did.  However, when I restarted, it says that X is not configured properly, and the GUI is not available. It gives me the option to configure X, but I honestly don't know what to do there.

So basically, I turned my system into a DOS box.

Worse comes to worst, I can simply reinstall, as I won't be losing anything but time, but I'm hoping there is a way to do this without reinstalling...

Thanks to anyone who can help.

-bg

edit: I guess this will have to wait for the morning...it's getting late...

---

### Post by slimdog360 on 2006-10-26
```
sudo apt-get remove gnome-compiz-manager compiz-freedesktop compiz-freedesktop-gnome
```

```
sudo nano /etc/X11/xorg.conf
```
remove the line you added
```
Option "AddARGBGLXVisuals" "True"
```

save it and restart x

if you were lucky enough to create a backup of your xorg.conf file, copy it back to its original state rather then editing it as above. You never know, you may have indavertently changed something you didnt mean to change. I know that the howto didnt say to create a backup though.

---

### Post by tubasoldier on 2006-10-26
> **bg1256 said:**
> 
So basically, I turned my system into a DOS box.


A DOS box? That might be true if you had a pile of garbage Command Line Interface that only had a few meager commands. Good thing you actually still have a Command Line Interface that has loads of commands to still run your system.

---

### Post by H.E. Pennypacker on 2006-10-26
bg1256, you don't have much to worry about.  Keep in mind that Linux, unlike Windows, comes in different "parts."  You may remember that Linux is not an operating system.  It's actually the kernel of an operating system.  If you don't quite understand this, check out Wikipedia.

X is another "part" of GNU/Linux.  It doesn't affect your personal files and other files of importance.  It only affects your ability to use a graphical user interface.

You'll be able to fix this problem, but the fix will have be through CLI (command line interface) until you get your X back.  Learn more about X at Wikipedia.

---

