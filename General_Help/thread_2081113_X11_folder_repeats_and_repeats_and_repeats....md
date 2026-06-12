---
title: "X11 folder repeats and repeats and repeats..."
date: 2012-11-06
forum: General Help
---

### Post by RogerDavis on 2012-11-06
I have a folder /usr/bin/X11 that has MANY copies of itself as sub folders. I quit counting at 25, but it appears to go on forever. 

All appear to be exact copies of /usr/bin.

1) How did they get there?
2) How can I get rid of them?
3) Can I just delete them, or will that wreck something?
4) If I do delete or otherwise lose them, how can I make sure they don't come back?
5) Any idea of what function they do/did?

---

### Post by mc4man on 2012-11-06
/usr/bin/X11 is just a symlink to /usr/bin which contains the X11 symlink so yes you could open it ad nauseam. 
Nothing to worry about, bit of explain
[http://ubuntuforums.org/showthread.php?t=1568381](http://ubuntuforums.org/showthread.php?t=1568381)

More specific
[http://ubuntuforums.org/showpost.php?p=12224020&postcount=9](http://ubuntuforums.org/showpost.php?p=12224020&postcount=9)
(if you were to remove the symlink probably nothing bad would happen but really no reason to

---

### Post by lykwydchykyn on 2012-11-06
It's not an actual folder, it's a symlink to the same folder.  That's why it appears to have endless copies of itself inside itself.

It's probably there because once long ago some binaries were in /usr/bin/X11, but later got consolidated to /usr/bin; but becaue some creaky old software might expect them at /usr/bin/X11, they made a symlink so it could find them.

Just leave it be, it hurts nothing and takes up no space.

---

### Post by RogerDavis on 2012-11-06
So if I delete them just because it's untidy and they annoy me, all that would be affected is "some creaky old software"?

Is there any way to find what "creaky old software" did this?  Then I could check to see if it's still installed, or if I can just trash it.

Thanks!

---

### Post by stinkeye on 2012-11-06
Just leave it as it is.
There isn't multiple files to delete.

---

### Post by RogerDavis on 2012-11-06
OK, just so I know:
1) Is there any way to find what software did this?
2) Is there a way to prevent this or something similar in the future?

---

### Post by lykwydchykyn on 2012-11-06
It's probably just that way by default.

It's really not a problem.  Understand:  There are not endless folders full of files.   Just one symlink back to the same folder.

I'd suggest leaving it be, or you'll likely have worse annoyances than an untidy-looking /usr/bin.

EDIT: according to apt-file, it's installed by the x11-common package.  I wouldn't recommend removing that ;).

---

### Post by RogerDavis on 2012-11-06
I don't see a direct reference to the x11-common package.  

I see many references includint X11, none of which seem to point to /usr/bin/X11.  A sampling of each type is below:
-------------------------------------------------
xkb-data: /usr/share/X11/xkb/symbols/de
xkb-data: /usr/share/X11/xkb/symbols/digital_vndr/lk
xkb-data: /usr/share/X11/xkb/symbols/macintosh_vndr/apple
xkb-data: /usr/share/X11/xkb/symbols/nokia_vndr/rx-44
xkb-data: /usr/share/X11/xkb/symbols/sun_vndr/ara
xkb-data: /usr/share/X11/xkb/symbols/terminate
xkeycaps: /etc/X11/app-defaults/XKeyCaps
xlbiff: /etc/X11/app-defaults/XLbiff
xless: /etc/X11/app-defaults/XLess-color
xloadimage: /etc/X11/Xloadimage
xlockmore: /etc/X11/Xresources/xlockmore
xmabacus: /etc/X11/app-defaults/Abacus
xmem: /etc/X11/app-defaults/XMem
xmix: /etc/X11/app-defaults/XMix
xmotd: /etc/X11/app-defaults/XMotd
xmpi: /etc/X11/app-defaults/XMPI
xmpuzzles: /etc/X11/app-defaults/Barrel
xonix: /etc/X11/app-defaults/Xonix/Xonix.ad
xorg-docs: /usr/share/X11/doc
xorg-sgml-doctools: /usr/share/sgml/X11/dbs/masterdb.html.xml
xosview: /etc/X11/app-defaults/XOsview
xpaint-dev: /usr/include/X11/Xaw3dxft/AllWidgets.h
xpat2: /etc/X11/de_DE/app-defaults/XPat
xpuzzles: /etc/X11/app-defaults/Barrel
xscreensaver-gl: /etc/X11/app-defaults/XScreenSaver-gl
xserver-xorg-core: /usr/share/X11/xorg.conf.d/10-evdev.conf
xshisen: /etc/X11/app-defaults/XShisen
xsok: /etc/X11/app-defaults/XSok
xsunpinyin: /etc/X11/xinit/xinput.d/xsunpinyin
xsysinfo: /etc/X11/app-defaults/XSysinfo
xtel: /etc/X11/app-defaults/XTel-color
xterm: /etc/X11/app-defaults/XTerm-color
xtightvncviewer: /etc/X11/app-defaults/Vncviewer
xtrans-dev: /usr/include/X11/Xtrans/transport.c
xtron: /etc/X11/app-defaults/Xtron
xutils-dev: /usr/lib/X11/config/Amoeba.cf
xvile: /etc/X11/app-defaults/XVile
xvkbd: /etc/X11/app-defaults/XVkbd
xwatch: /etc/X11/app-defaults/XWatch
xxgdb: /etc/X11/app-defaults/XDbx
xxkb: /etc/X11/app-defaults/XXkb
z88dk-data: /usr/share/z88dk/include/X11
-----------------------------------------------
This is maybe 5% of the file.

Do I have a different source for all this stuff than you?

Does it still look useful?

Thanks!

---

### Post by lykwydchykyn on 2012-11-06
I don't know what file you're looking at or referring to.  apt-file is a command that can tell you to which package a file belongs.

I installed apt-file, ran:
```

sudo apt-file update
apt-file find /usr/bin/X11

```

And it told me the symlink came from the x11-common package.

---

### Post by RogerDavis on 2012-11-06
Now I understand...

---

### Post by drmrgd on 2012-11-06
As mc4man says, it's a symbolic link to the /usr/bin folder.  If you look at the detailed listing:

```
$ ls -l X*
-rwsr-sr-x 1 root root   10184 Mar 22  2012 X
lrwxrwxrwx 1 root root       1 Jul 27 16:13 X11 -> .
```

You see that the symbolic link points to the current directory.  If you're bored one day, you can try following it for a while.  I don't think you'll find the end, though :D

At any rate, like others say, it's not worth messing with.

---

### Post by RogerDavis on 2012-11-06
I do understand, but it seems to me about the worst possible way to do it.

---

### Post by stinkeye on 2012-11-06
> **RogerDavis said:**
> I do understand, but it seems to me about the worst possible way to do it.
What I don't understand is how is the existence of this symlink folder
causing you annoyance?

---

### Post by RogerDavis on 2012-11-06
It's been a long time since I've done programming but there MUST be better ways to do it than to make a folder that calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, ... my fingers are getting tired.

---

### Post by stinkeye on 2012-11-06
It simply reroutes anything looking for 
/usr/bin/X11
to
/usr/bin
...so it's not calling itself.

---

### Post by mc4man on 2012-11-06
> **RogerDavis said:**
> It's been a long time since I've done programming but there MUST be better ways to do it than to make a folder that calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, calls itself, ... my fingers are getting tired.

It doesn't, it only links to /usr/bin
(actually the symlink is generic, it links to whatever dir. it's in, if you were to copy it your Documents folder then when opened from your Documents folder you'd see your Documents folder, ect.

What's repeating is _you_, you're _browsing_  to the same target dir. over & over,  not unlike   chasing one's tail

---

