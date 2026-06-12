---
title: "more nvidia kernel fun!"
date: 2004-11-10
forum: General Help
---

### Post by maus on 2004-11-10
Heya, I've been using Ubuntu for about a month or so now, and I love it. I decided this week, however, that maybe it was time to build me a custom kernel. Mainly, I'd like support for my SNES-LPT controller, and having a K7/Athlon XP-customized kernel can't hurt, right?

So I compiled one a few days ago (I always do --append-to-version=.07nov2004... or whatever the date is), and had some problems stemming from the fact that I didn't build ReiserFS support into the kernel, but rather as a module. Oops! Okay, so I fixed that, and went back through, making sure to have all my ducks in a row.

I built, installed, rebooted, and... hey! It loaded Ubuntu. Fantastic, both ReiserFS and IDE support were working.

Then it went to start X.... and I started having myself a problem. So I posted about it over in some other forums I frequent, and was told I need to compile the nVidia module. So I booted back into my new kernel, and did this at the CLI:

```
apt-get install nvidia-kernel-common
module-assistant auto-install nvidia
apt-get install nvidia-glx
dpkg-reconfigure xserver-xfree86
```

...to no avail. What am I doing wrong here?


Oh, also, I'm a former Windows desktop user (aren't we all?). I've been using Gentoo on my headless fileserver for awhile, but I'm pretty clueless when it comes to X and Debian. I like apt a whole lot, though. One thing I'm wondering: is there a utility similar to the Windows msconfig? I have things like Gnocatan installed that starts up the meta-server daemon at every startup... and I don't want that. How can I stop it without uninstalling gnocatan?

---

### Post by Enygma on 2004-11-10
Hey,

I had a similar problem when I compiled a patched kernel, check out p!=f's reply on this thread:
[http://www.ubuntuforums.org/showthread.php?t=3408](http://www.ubuntuforums.org/showthread.php?t=3408)

It worked for me anyway.

---

### Post by strips on 2004-11-10
If you are compiling your own kernel end want to use the nvidia kernel module that comes with Ubuntu you need the nvidia-kernel-source package. 

It's placed in /usr/src, unpack it and compile it.

Remember /usr/src/linux should point to your kernel source.

BUT... personally I prefer to use the Nvidia installer downloaded directly from Nvidia. 

Nvidia has a newer driver than the one in the Ubuntu repository. This new driver works for Kernel 2.6.9 , wich the Ubuntu one doesn't.

---

### Post by maus on 2004-11-10
Ahh, I'm probably doing things in the wrong order, then. Unless I'm not? Oh, I'm not used to Debian at all. So I should run module-assistant before I build my custom kernel, after I build my custom kernel, or while my custom kernel is running?

And will it even work in 2.6.9, or do I need to use the nVidia install script? I think that's what I did for my current install, in order to get OpenGL (and thus UT2004) working. 



While we're at it, is there a nice tool for cleaning up the clutter in my /boot/grub/menu.lst? What with all of these failed installs, I'm getting about six kernels in my bootup menu. I can erase them manually, I suppose.

---

### Post by maus on 2004-11-10
Uh-oh! I did what that fellow said in the other thread, and now X doesn't work no matter what kernel I boot! I'm very close to putting the Ubuntu CD in and reinstalling everything... but I'd like to avoid that if possible, and solve this problem. I think one problem I'm having is general clutter; I've tried to compile about ten or eleven kernels now, and I've tried to install the nvidia module/driver stuff about five times. How can I start with a clean slate?
Or is that what I even want to do? I'm supposing that the best course of action right now would be to try and wipe everything down and compile a new, working kernel.
Are there any logs or whatnot that could help diagnose my problem here? I'm at my wits' end, and it's only through playing Katamari Damacy over on my PS2 that I haven't thrown my computer at things (e.g. wall, window).

---

### Post by Enygma on 2004-11-11
Hey,

You should be able to boot the original kernel by editing /boot/grub/menu.lst
Change the default to whatever entry the original kernel is. 

Run 
sudo dpkg-reconfigure xserver-xfree86
to reconfigure X
Select 'nv' instead of 'nvidia' and make sure that 'GLcore' and 'dri' are enabled when you get to them. Everything else should just be the default answer.

This should at least get you running X which is better than nothing.

---

### Post by maus on 2004-11-11
Actually, I solved the problem overnight! I had an idea while I was driving around town, and I spent a good twenty minutes before I got home wanting to try it.

It was really quite simple.

I ran one of these
```
apt-cache search kernel
```

And apt-get removed everything that wasn't the kernel I was using. I did the same with 'apt-cache search nvidia'. Once all of that was done, I installed the 2.6.9 source, made menuconfig, and dpkg/kpkg -i'd it. Booting into my brand new kernel, I ran the nVidia .run script dealie.

And now I'm using X again! And OpenGL acceleration is working. So. I think this calls for some bzFlag!

---

