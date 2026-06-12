---
title: "Xorg problem"
date: 2006-10-28
forum: General Help
---

### Post by koulanji on 2006-10-28
I was messing around with xorg.config file trying to install compiz, but when i restarted the gdm, the x server could not start up, and I got the following errors:

Parse error line 125 of section device in the file etc/x11/xorg.conf The option keyword requires 1 or 2 quoted strings to follow it

Parse error on line 191 section DRI in file etc/x11/xorg.conf section requires a quoted string to follow it. 

Then i have to do my log in through text editor and I am transported to the terminal. My question is: how I do restore everything to the default setting. Thanks. If you're wondering where I got my instructions for the compiz installation, I got them here  [http://www.oliyiptong.com/blog/2006/10/28/ubuntu-610-edgy-eft-upgrade-plus-compiz-goodness/](http://www.oliyiptong.com/blog/2006/10/28/ubuntu-610-edgy-eft-upgrade-plus-compiz-goodness/) and here
[http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

A speedy reply would be greatly appreciated, Thank you

:-D

---

### Post by ~LoKe on 2006-10-28
Just type this in the console...

```
nano /etc/X11/xorg.conf
```

And follow along until you get to the problematic section and fix the quotation problem.

---

### Post by beerfan on 2006-10-28
If you were lucky to have edited it with gedit there may be a backup (xorg.conf~).

---

### Post by koulanji on 2006-10-28
> **~LoKe said:**
> Just type this in the console...

```
nano /etc/X11/xorg.conf
```

And follow along until you get to the problematic section and fix the quotation problem.


Can you get a little more specific about how to restore the default settings thru nano, since there is absolutely no text in it.

---

### Post by ~LoKe on 2006-10-28
> **koulanji said:**
> Can you get a little more specific about how to restore the default settings thru nano, since there is absolutely no text in it.

I wasn't trying to help you restore the default settings, I was just trying to tell you how to fix the problem you're having.  Apparently you're missing a quotation mark, or something, and going into the file and adding one would fix your problem.

You could also use a backup, there's probably one called xorg.conf~ so...

```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```
If for some reason that doesn't work...
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by koulanji on 2006-10-28
> **~LoKe said:**
> I wasn't trying to help you restore the default settings, I was just trying to tell you how to fix the problem you're having.  Apparently you're missing a quotation mark, or something, and going into the file and adding one would fix your problem.

You could also use a backup, there's probably one called xorg.conf~ so...

```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```
If for some reason that doesn't work...
```
sudo dpkg-reconfigure xserver-xorg
```

Neither works. i tried reconfiguring the xserver, but after reconfiguration, I still get the text mode. Do i need to restart the gdm after?

---

### Post by koulanji on 2006-10-28
> **~LoKe said:**
> I wasn't trying to help you restore the default settings, I was just trying to tell you how to fix the problem you're having.  Apparently you're missing a quotation mark, or something, and going into the file and adding one would fix your problem.

You could also use a backup, there's probably one called xorg.conf~ so...

```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```
If for some reason that doesn't work...
```
sudo dpkg-reconfigure xserver-xorg
```

I got it; I put in the wrong graphics card driver like an ***. Thank you man. :)

---

### Post by Blutack on 2006-10-28
Rebooting would probably do the trick.  If not, go through the dpkg-reconfigure again and check carefully that the stuff us normal humans actually understand makes sense for your hardware (right graphics card etc).  Good luck!

---

