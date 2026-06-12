---
title: "sketch up software is not working  with wine"
date: 2007-02-21
forum: General Help
---

### Post by kankana on 2007-02-21
i downloaded the sketchup software which is GoogleSketchUpWEN.exe i typed
wine GoogleSketchUpWEN.exe in terminal
but in the terminal it displays as
wine: could not load L"c:\\windows\\system32\\GoogleSketchUpWEN.exe" : Module not found

can anyone help me solve the problem

---

### Post by yabbadabbadont on 2007-02-21
You might check the WINE appdb to see how others have gotten it to work (or for a list of things that don't work).

[http://appdb.winehq.org/appview.php?iAppId=1815](http://appdb.winehq.org/appview.php?iAppId=1815)

---

### Post by steven8 on 2007-02-21
You can open a terminal and type winefile.  This will open a wine windows-type file browser.  Browse to your exe and double click it.  Just like windows.

---

### Post by bapoumba on 2007-02-21
Moved to "General Help".

---

### Post by gudy1024 on 2007-02-24
I tried running sketchup.... it only gives a window "openGL needed" it seems version 4.0 was able to be runned under wine, but the new version 6... not yet
previous releases of sketchup
[http://www.sketchup.com/index.php?id=362](http://www.sketchup.com/index.php?id=362)

---

### Post by futz on 2007-03-10
I just installed SketchUp 6 and it works ok. Has some quirks that aren't there when running in windoze, but it is useable. Menus don't display right, tho you can get them to sorta work with some mouse-wiggling and clicking where you know the menu has to be, but isn't being displayed.

In the terminal I start it from I get MANY of these:
```
fixme:cursor:create_cursor Currently no support for cursors with 32 bits per pixel
```
That probably explains the quirks.

Oh! It just crashed. Guess it may be a bit flaky in Wine. More use will tell...

---

### Post by soholingo on 2007-03-19
I use version 6 of Sketchup to and my experiences are similar.  It is so close to working it isn't even funny...

---

### Post by ramjet_1953 on 2007-03-20
Works great using VirtualBox!

Regards,
Roger :cool:

---

### Post by futz on 2007-03-20
> **ramjet_1953 said:**
> Works great using VirtualBox!

Regards,
Roger :cool:
Awesome! Installing VirtualBox now. Thanks Roger! :mrgreen:

---

### Post by originalsurfmex on 2007-12-14
thats interesting - from what i've been reading virtualbox and others can't get 3d accelleration (only vmware fusion) - so for me sketchup has been very very sub-par on virtualbox.

did you do any tricks to make it work?

---

### Post by ArtInvent on 2008-02-12
I've been running VirtualBox with Sketchup 6 on Gutsy. It's stable at least and everything works but it's dog slow because of no 3D. However, it's less aggravating than under wine up to 0.9.55 because it just hangs and crashes and certain things don't work right.

Right now it's kind of a slow horse race: will some virtualization package come along that can do 3D really well - or will Wine get this app going. I would bet on Wine because at one point around Wine 0.9.49 in Feisty it worked pretty much perfect. And Wine (when it works) is way less hassle and overhead than a virtual OS.

---

### Post by phonicboom on 2008-04-22
any big success stories yet?

---

