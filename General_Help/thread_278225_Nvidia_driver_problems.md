---
title: "Nvidia driver problems"
date: 2006-10-16
forum: General Help
---

### Post by raymacey on 2006-10-16
I'm trying to install Nvidia drivers, and I'm having problems.  Before anyone asks, I have read the sticky regarding Nvidia drivers at the top of the forum, however I'm not sure if it's relevant to me, and that in turn is part of my question...

In any case, I'm running dapper and a GeForce FX 5200.  I've downloaded the nvidia beta drivers from nzone.com, as well as tried the nvidia-glx package from the repository. Unfortunately, whichever one I try, I get the same problem.  If I shut down x and then restart it, I can get back in to gnome or KDE just fine.  

Once I restart the system however, it simply won't load X, and I get [the error mentioned in the sticky thread]("http://ubuntuforums.org/showthread.php?t=257459") about being unable to load X.  

I don't think that's the problem however, as I've done a complete re-install early this month and encountered the exact same problem when I attempt to install either the beta drivers or the nvida drivers package, and this was well and truly after the dates listed in the sticky.  In any case, just to be sure, I've followed the instructions in that thread in any case, and that hasn't helped.

The only way I'm able to get X to load again is to edit xorg.conf and replace the nvidia drivers with nv drivers.

Any ideas on what to try next would be greatly appreciated.

---

### Post by jazzgossen on 2006-10-16
I encountered the same issue after installing the beta drivers in Edgy. Take a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=275842&highlight=nvidia"). The problem is that Ubuntu tries to fix a "broken" package that it detects after you install the beta drivers manually.

---

### Post by _simon_ on 2006-10-16
The way I install them is:

Add the following to /etc/default/linux-restricted-modules
```

DISABLED_MODULES="nv"

```

Then download:

Current Stable
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

or

New Beta
[http://www.nzone.com/object/nzone_downloads_rel70betadriver.html](http://www.nzone.com/object/nzone_downloads_rel70betadriver.html) (scroll to bottom and choose correct one)

Restart machine, enter grub menu and run the recovery mode (or whatever it is called) option.

login as yourself at the prompt.

then:

```

sudo sh /path/to/installer.run

```

Then just follow the prompts.

---

### Post by raymacey on 2006-10-16
```

DISABLED_MODULES="nv"

```

Thanks heaps guys.  That was the culprit right there.  All working now.  I should have saved myself days of pain and asked earlier :)

---

### Post by headchange on 2006-10-18
just wanted to thank you for this post, i tried to get my drivers for my nvidia card for couple weeks.  after i disabled the module nv, i restarted and booted up into the recovery mode and installed the drivers but it needed xorg-dev so i had to isntall that, but after that it installed fine, but it was screwing up saying no more processes in this run level, so i had to boot back into recoverey mode and went looking around in the xorg.config file, and the damn driver for the graphics was still on nv, so i changed it to nvidia and viola as soon as i saw the splash screen i was very happy, because i almost formatted, thanks again for this post

---

