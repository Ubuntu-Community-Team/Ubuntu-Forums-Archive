---
title: "XGL and fonts"
date: 2006-07-31
forum: General Help
---

### Post by jeremytaylor on 2006-07-31
Hi,

Some information:

I've got XGl and Compiz all set up on my laptop and love all the whizzy effects. I'm using the drivers from ati for my x600 mobility card as I couldn't get the ubuntu ones to work and I'm having to use my own kernel as my asus laptop won't boot with the stock ubuntu one. 

Now for the problem:

I have lots of problems with X11 fonts. In Emacs all the characters appear as little boxes unless I specify a font path with emacs -fn and then I can't find oen that looks remotely like the default one. 

Stellarium has similar problems with fonts (more little boxes).

R won't do any plotting and complains about the lack of X11 fonts. 

I have never changed my fontpath in the xorg.conf file and it seems to list a number of appropriate sounding fonts. 

So who can suggest something to help? What dumb thing have I done or not done?
Thanks
Jeremy

---

### Post by jeremytaylor on 2006-07-31
I've got the R working by using the command
xset fp rehash

but it doesn't help the other problems

---

### Post by shoagun on 2006-08-02
I'm having the same problem.  I got xgl+compiz working but emacs now shows boxes as the font.  I've been searching for solutions on forums and none of the ones I've found so far seem to apply.  

Here is what my xorg.conf shows:

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


has anyone fixed this problem?

---

### Post by shoagun on 2006-08-16
Sorry, but I'm bumping this because it seems like such a stupid little problem that I'm sure someone out there must know a solution.  

To reiterate, I have installed the latest version of emacs along with all the extra goodies and such.  When I start a session with xgl+compiz, I need to specifiy a font (with -fn) or all I get is boxes.  If I start a normal Gnome session, I don't have the problem.

---

### Post by ufalcon on 2006-09-25
I've got the same font issue, and it's a total pain!  I want to run emacs off of a remote system to do work, but the font, naturally, is not available.  I'm actually running Edgy, but I get the following when I run emacs (remote or local):

~$ emacs
Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct

If somebody can figure this out, I would be elated!!!!

---

### Post by gotgenes on 2006-10-12
Try creating the following symlinks
```

sudo ln -s /etc/X11/rgb.txt /usr/lib/X11/rgb.txt
sudo ln -s /etc/X11/rgb.txt /usr/share/X11/rgb.txt
sudo ln -s /etc/X11/rgb.txt /usr/X11R6/lib/X11/rgb.txt

```
I'm not sure if all of those are necessary but they seem to have fixed the issue for me.

[COLOR="Red"]**EDIT**[/COLOR]: I take that back, **the above doesn't work**. Sigh.

---

### Post by dahen on 2006-10-14
If you haven't already figured it out, just edit your /usr/bin/startxgl.sh and add font paths (-fp) according to your xorg.conf.

My script looks like:
#!/bin/sh
Xgl -fullscreen :1 -ac -fp /usr/share/X11/fonts/misc,/usr/share/X11/fonts/cyrillic,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
exec gnome-session

---

### Post by orbe on 2008-01-16
Jeremy,

I'm working with Ubuntu 7.10 with XGl and ati 200M card. Yesterday, when finally I can configure XGl I had the same problem with fonts in emacs: I can't see anymore than squares, I try uninstall and install again it, but it didn't work. After that, I install through Synaptic emacs metapackage which installs emacs22 instead of emacs 21.4 and it works without problem!

I hope that it can be useful for you.

Oscar

> **jeremytaylor said:**
> Hi,

Some information:

I've got XGl and Compiz all set up on my laptop and love all the whizzy effects. I'm using the drivers from ati for my x600 mobility card as I couldn't get the ubuntu ones to work and I'm having to use my own kernel as my asus laptop won't boot with the stock ubuntu one. 

Now for the problem:

I have lots of problems with X11 fonts. In Emacs all the characters appear as little boxes unless I specify a font path with emacs -fn and then I can't find oen that looks remotely like the default one. 

Stellarium has similar problems with fonts (more little boxes).

R won't do any plotting and complains about the lack of X11 fonts. 

I have never changed my fontpath in the xorg.conf file and it seems to list a number of appropriate sounding fonts. 

So who can suggest something to help? What dumb thing have I done or not done?
Thanks
Jeremy

---

