---
title: "Hardy Num Pad Stop Working"
date: 2008-05-10
forum: General Help
---

### Post by trmentry on 2008-05-10
I have a very odd thing that just started on my basicly stock install of Hardy on my laptop.  

I'm using a docking station so have an extenal keyboard hooked up to the laptop.   The num pad was working fine for a couple of weeks, then starting this week, after booting and it doing a disk check at boot, the num pad stops working when I reach the desktop.

The really odd thing is the num pad works at the logon screen.  But when I get to the full gnome desktop, its dead.  I've tried with both num light on and off.  And still nada.
  
I've tried removing my keyboard layout and re-adding but still no joy.

I have USA as the layout.

Any ideas?

---

### Post by Xgen on 2008-05-10
Install or reinstall Synaptic--->numlockx?

---

### Post by trmentry on 2008-05-10
> **Xgen said:**
> Install or reinstall Synaptic--->numlockx?

No joy. :(

What's Plan B?  ;)

---

### Post by trmentry on 2008-05-13
well I wiped my laptop and reinstalled Hardy and my numlock works fine now.  

My guess is an update borked it or a file got borked... but not sure which.

---

### Post by F0EHammer_dg on 2008-05-14
I had a similar issue when upgrading from gutsy.  Installed numlockx... no love.  The fix was this:

Go to System -> Preferences -> Keyboard
Select "Mouse Keys" tab
Uncheck "Allow to control the pointer using the keyboard"

This may not be everyone's issue but an easy way to find out is if the numpad keys move the pointer around.

EDIT:  This has also been discussed [elsewhere]("http://ubuntuforums.org/showthread.php?t=771377")

---

### Post by jonrwads on 2008-06-06
> **F0EHammer_dg said:**
> I had a similar issue when upgrading from gutsy.  Installed numlockx... no love.  The fix was this:

Go to System -> Preferences -> Keyboard
Select "Mouse Keys" tab
Uncheck "Allow to control the pointer using the keyboard"

This may not be everyone's issue but an easy way to find out is if the numpad keys move the pointer around.

EDIT:  This has also been discussed [elsewhere]("http://ubuntuforums.org/showthread.php?t=771377")

Thanks for adding on to this thread.  It just solved my problem.

---

### Post by Dr_Snapid on 2008-06-18
> **F0EHammer_dg said:**
> I had a similar issue when upgrading from gutsy.  Installed numlockx... no love.  The fix was this:

Go to System -> Preferences -> Keyboard
Select "Mouse Keys" tab
Uncheck "Allow to control the pointer using the keyboard"

This may not be everyone's issue but an easy way to find out is if the numpad keys move the pointer around.

EDIT:  This has also been discussed [elsewhere]("http://ubuntuforums.org/showthread.php?t=771377")

Thanks!

---

### Post by katcw on 2008-06-28
Thanks for the tip!  It worked beautifully!!!

> **F0EHammer_dg said:**
> I had a similar issue when upgrading from gutsy.  Installed numlockx... no love.  The fix was this:

Go to System -> Preferences -> Keyboard
Select "Mouse Keys" tab
Uncheck "Allow to control the pointer using the keyboard"

This may not be everyone's issue but an easy way to find out is if the numpad keys move the pointer around.

EDIT:  This has also been discussed [elsewhere]("http://ubuntuforums.org/showthread.php?t=771377")

---

### Post by RicJD on 2008-07-05
> **jonrwads said:**
> Thanks for adding on to this thread.  It just solved my problem.

Dude that bugged me soo much, thanks!

---

### Post by kommissar on 2008-08-18
That was my problem too.  Thank you!

---

### Post by mjstander on 2008-12-02
that solved my problem

---

