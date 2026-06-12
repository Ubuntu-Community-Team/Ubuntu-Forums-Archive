---
title: "[SOLVED] Why does the console font change during boot?"
date: 2008-02-20
forum: General Help
---

### Post by dwasifar on 2008-02-20
This is not a problem so much as just curiosity.

When first booting, before the usplash, you get the black console screen reporting the kernel, the file system, etc.  I notice that for a second or two, just before the usplash comes up, the font changes.  It does that on every ubuntu box I have.  If the usplash drops back to console during boot (for an fsck, say), the font is the same as what it changed to before the usplash came up.

Why does this happen?  I'm curious.

---

### Post by freelinuxhelp on 2008-02-20
I've actually seen this on every Linux machine I've worked on... all the way back to slackware in 1996. Don't know what causes it.

---

### Post by freelinuxhelp on 2008-02-21
My boss thinks that it changes when the OS system fonts are loaded into memory. Prior to this, it's using the default font in the motherboard or the video card.

---

### Post by koenn on 2008-02-21
yep, 
you can actually see that happen if you turn of the boot spalsh screen or boot recovery mode :
you get a message
```
setting up console font
setting up per-VC font
  /dev/tty2
  /dev/tty3
  ...
```
and at that same moment, you see the fonts being replaced by better-looking ones.

---

### Post by freelinuxhelp on 2008-02-21
Hmm. Glad to know what's going on.
I manage a bunch of SCO boxes for work, but I don't remember ever seeing them do this. Does anyone know if this behavior is unique to Linux?

---

### Post by koenn on 2008-02-21
It's a hardware/firmware thing, i.e. the system uses a font stored in ROM on the VGA card untill it's told to use something else. I remember seeing the same on MS_DOS systems. The "small caps" M really stands out - untill you load a console driver (or do something with MODE CON, don't remember exactly) and get a smooth m .

---

### Post by The Cog on 2008-02-21
> **koenn said:**
> 
and at that same moment, you see the fonts being replaced by better-looking ones.
That might be your opinion, but it isn't mine. I just don't use the tty consoles often enough to be driven to the effort of finding out how to load a better font.

---

### Post by koenn on 2008-02-21
well, its a* fact * that the fonts get replaced. 
we're going to have an argument now about whether or not the the replacement is actually better-looking ? go ahead - I won't be listening.

---

### Post by tmb_ayebe on 2008-02-24
My opinion is that the original font is nicer. Is there any way to stop the change from happening?

---

### Post by pointone on 2008-02-24
You could fiddle around in "/etc/init.d/console-screen.sh".

---

### Post by freelinuxhelp on 2008-03-08
dwasifar, wanna mark this thread solved?
The option is under the Thread Tools menu.

---

