---
title: "Stuck at kdm"
date: 2006-12-29
forum: General Help
---

### Post by pgatrick on 2006-12-29
Somehow I've managed to completely mess my computer up, and now at the kdm login screen it just starts to login in then reloads the login page. Eventually the whole xserver will just crash if I keep trying to log in. I'm not sure what part of it I've managed to mess up, but it won't log me into a kde, or gnome session, just keeps taking me back to the login screen. I've tried gdm logging into either, but it apparently doesn't work for me either anymore for some unknown reason. Just takes me to a fairly blank screen with a terminal window (no borders or anything) and pops up some error about not being able to start a child process for the terminal.. Does that regardless of if I'm trying to get into gnome or kde. Only way I can mange to get on is to run startx while root. I still get various errors, but it seems to work.
Ok so anyway, there are a few things I've done lately that I can think of which might have caused this.
I was trying to install the drivers for my aiptek tablet, and I heard they could cause problems with the xserver, which they did, I wouldn't be able to switch between virtual terminals or whatever. That had never kept me from being able to restart or login though. I unplugged my tablet, removed the drivers, and put my xorg.conf back to how it was before, but that didn't seem to help at all.
The other thing, right before this started happening, I (stupidly apparently) tried to open a 211Mb .tif file in konqueror.. Which slowed things down so much I chose to restart my computer.. And that's when this happened. Maybe kde can't load because it's trying to restore what was going on when it closed( konqueror and the huge file)? Don't know what to do about that, and I deleted the file to see if that would help.. It didn't.
/var/log/Xorg.0.log ends with something about being unable to find some /usr/lib/xserver/SecurityPolicy file, and /var/log/kdm.log adds to that something about QImage being null and some other similar things..
Sorry for the long rambling post, but I'm out of ideas on how to fix this.. ](*,)

---

### Post by pgatrick on 2006-12-29
I've now reinstalled both kdm and xorg, but it's made absolutely no difference. I guess I'll try just reinstalling all of kde now, and hopefully that will work. If not, I guess I'll just reinstall my whole system.

---

### Post by costis on 2006-12-31
My problem is that after hitting "Switch User" the screen goes totally blank. *Some times* I can see the actual login screen pressing Ctrl+Alt+F5,  Ctrl+Alt+F6 and then  Ctrl+Alt+F7. But most of times this doesn't work either.
I have tried to reinstall/reconfigure gdm & xserver, and also append vga=791 as a kernel boot parameter but nothing of them works. :(

> **pgatrick said:**
> /usr/lib/xserver/SecurityPolicy file, and /var/log/kdm.log adds to that something about QImage being null and some other similar things..
I think the correct file is /usr/share/doc/xserver-xorg-core/SecurityPolicy (found after doing $ locate SecurityPolicy)
but none of the /etc/gdm files contains a setting for this.... Where that might be?

I would also like to add from gdm log```

The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
```
I would like to solve these issues, too...
```
~$ dmesg | grep alloc
[   28.576741] PCI: Failed to allocate mem resource #6:10000@f4000000 for 0000:01:00.0
[   29.028786] Cannot allocate resource for EISA slot 1
[   29.028794] Cannot allocate resource for EISA slot 2
[   29.028806] Cannot allocate resource for EISA slot 4
```
I attach my ~$ lshw.

Thank you all and happy new year!... :D

---

### Post by costis on 2006-12-31
What [about]("http://groups.google.com/group/linux.debian.user/browse_thread/thread/fd47efc7b907b01e/4846d2c47354bbab?lnk=st&q=error+opening+security+policy+file+%2Fusr%2Flib%2Fxserver%2FSecurityPolicy&rnum=3&hl=en#4846d2c47354bbab")
```
~$ sudo mkdir /usr/lib/xserver
~$ sudo ln -s /usr/share/doc/xserver-xorg-core/SecurityPolicy  /usr/lib/xserver/SecurityPolicy

```funny, uh?

---

