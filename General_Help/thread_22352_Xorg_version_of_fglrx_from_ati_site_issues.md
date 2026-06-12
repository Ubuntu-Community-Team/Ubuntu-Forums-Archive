---
title: "Xorg version of fglrx from ati site issues"
date: 2005-03-27
forum: General Help
---

### Post by teumima on 2005-03-27
Hi I downloaded from the ATI site the xorg version fglrx

which is: fglrx_6_8_0-8.10.19-1.i386.rpm

So I used alien and got the packagae:fglrx-6-8-0_8.10.19-2_i386.deb

When I do sudo dpkg - i fglrx-6-8-0_8.10.19-2_i386.deb

I get the following error:

amichai@bzq-179-124-6:~/downloads$ sudo dpkg -i fglrx-6-8-0_8.10.19-2_i386.deb
Selecting previously deselected package fglrx-6-8-0.
(Reading database ... 83738 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.10.19-2_i386.deb) ...
dpkg: error processing fglrx-6-8-0_8.10.19-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xli bmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-6-8-0_8.10.19-2_i386.deb
amichai@bzq-179-124-6:~/downloads$ sudo dpkg -i fglrx-6-8-0_8.10.19-2_i386.deb
(Reading database ... 83738 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.10.19-2_i386.deb) ...
dpkg: error processing fglrx-6-8-0_8.10.19-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-6-8-0_8.10.19-2_i386.deb


Note how I tried it twice

---

### Post by Dracontopes on 2005-03-27
Don't know if it is possible, but what if you uninstall xlibmesa-gl?

---

### Post by bobmitch on 2005-03-27
Do:

```
sudo dpkg -i --force-overwrite fglrx-6-8-0_8.10.19-2_i386.deb
```

---

### Post by teumima on 2005-03-27
Thanx bru

I did it. 

Now do I need to change anything else for it to work? Like in the xorg file? Do i look at the other forums same story?

---

### Post by Dracontopes on 2005-03-27
[QUOTE=teumima]Thanx bru

I did it. 

Now do I need to change anything else for it to work? Like in the xorg file? Do i look at the other forums same story?[/QUOTE]
 The problem will probably only get worse :) But the main things you have to do is run *fglrxconfig* which will create a XF86Config-4 file. When asked for the use of External AGP driver answer yes (atleast, that does the trick for me || this will enable the use of the kernel's agpgart module instead of the one supplied with fglrx which does not work, guess it's a bug). The XF86Config-4 file then has to be renamed to xorg.conf (you're using xorg right?) Best thing to do all this is from a console and not in X. 

(Small tip: install the most recent drivers from ati.com, they work better (more FPS) for me. Plus it will create a xorg.conf file instead of XF86Config-4 :) )

Oh and you will know if you have direct rendering in X by doing

```
glxinfo | grep rendering
```

Good luck! \\:D/

---

### Post by teumima on 2005-03-28
Hey guys

This ati thing was really bugging me. Couldn't figure it out for months. Anyway I spent a few hours chatting with the guy on irc.freenode.org #ati and there are quite a few things that need to be done that I haven't yet seen mentioned in many forums. I have 3d accel. graphics now, got rid of that annoying mesa gl it only mentions ati now and just played counter strike.

I'm planning to compiling a HOWTO. Maybe tonight.

For the impatient ones go ato #ati and hopefully you'll bump into helpful guys like I did, the one I bumped into was a Debian user so very convenient.

Be well

---

### Post by cedricthegreat on 2005-03-29
I found the following site,  with instructions and packages for debian maybe it's usefull to you guys.

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

I would be very interested to something like this specifically for Ubuntu.

---

