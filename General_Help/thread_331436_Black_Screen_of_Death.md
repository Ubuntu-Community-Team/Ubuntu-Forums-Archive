---
title: "Black Screen of Death"
date: 2007-01-04
forum: General Help
---

### Post by jtinfinite on 2007-01-04
Hi.  First time poster here.

Ok, it seems like I am in a rather large group of people who have similar problems, but I have not found a solution for this one yet.  I am running Ubuntu Dapper 6.06 on my desktop.
The desktop has a pretty neat nVidia 980 XGL workstation card in it, so I decided to use the proprietary drivers so that I could get the most out of it.  I tried a few different things, all of which did not work.  My latest effort has been to use the "envy" script to carry out the install.    Now on system start, after my BIOS screens and whatnot, I am greeted with a black screen.  However, I do hear the system bongo sound.  X logs show no errors.  I am confounded.  I should also note that I did have a spurious Wacom tablet detected and added to the xorg.conf file.  I commented out all references to it and now my logs show no errors associated with it.  Is there anyone out there who knows what could be causing this? ](*,)

Thanks,
JT

---

### Post by riven0 on 2007-01-04
:-k Alright, can you try hitting ALT + CTRL + F6 to get to the terminal. Then log in and type **startx**. What happens then?

---

### Post by jtinfinite on 2007-01-04
> **riven0 said:**
> :-k Alright, can you try hitting ALT + CTRL + F6 to get to the terminal. Then log in and type **startx**. What happens then?

This dumps the following error:

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit: unable to connect to X server
xinit: No such process (errno 3):  Server error.

---

### Post by riven0 on 2007-01-04
Okay, the first thing to do is try reconfiguring the xserver:

Get back to the terminal with CTRL + ALT + F6 and type:

> sudo dpkg-reconfigure xserver-xorg

Then reboot and see if that will fix it.

---

### Post by jtinfinite on 2007-01-04
No, that didn't work, unfortunately.  I get a black screen and the bongo sound.

I checked the Xorg.0.log for errors and apparently the Wacom tablet showed up again, so I commented out all of those sections and rebooted.

Black screen and the startup sound again.  I checked the log for errors.

cat Xorg.0.log | grep EE

returned nothing

and 

cat Xorg.0.log | grep WW

returned an warning that /usr/share/X11/fonts/cyrillic does not exist.

---

### Post by riven0 on 2007-01-04
:-k Okay, sometimes reinstalling the xserver helps. Try this instead:

> sudo apt-get install --reinstall xserver-xorg

---

### Post by jtinfinite on 2007-01-04
Hmm.  That's odd.  Xserver reinstall is throwing an error.

Temporary failure resolving 'archive.ubuntu.com'.

---

### Post by riven0 on 2007-01-04
Strange, see if you can  get on the net. Try this:

> ping google.com

---

### Post by jtinfinite on 2007-01-04
Ok, I managed to get it to work.  I think my internet access went wonky for a minute there.  Xserver reinstalled with no errors.  I still have the same problem, though.

---

### Post by khedron on 2007-01-04
Maybe if you post Xorg.0.log here, and maybe also /etc/X11/xorg.conf , we can see if X is the problem.

Just to clarify: you are able to hit Ctrl-Alt-F1 to go to a console, right? Or do you have to go into recovery mode?

If you can, you could try **killall Xorg** from the console and then do **startx**.

WRT Wacom, you can delete all the wacom sections from xorg.conf. Just delete all the wacom "InputDevice" sections, and delete the InputDevice entries from the "ServerLayout" section - that's the "stylus", "cursor" and "eraser" lines.

---

### Post by druhboruch on 2007-01-04
First try vesa driver in xorg.conf

Driver		"vesa"

---

