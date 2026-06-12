---
title: "Ubuntu won't load"
date: 2008-03-13
forum: General Help
---

### Post by guidemeintheeyesofblindne on 2008-03-13
I installed wubi/ubuntu. 

Now what?  The pc just reboots in windows.  Where do I go from here? 

I got windows xp home edition.

help?

---

### Post by ago on 2008-03-13
What version of Ubuntu did you use, and what version of windows do you use?

You should now use Wubi 8.04
If you are on windows XP make sure you have the permission to edit c:\boot.ini
If you are on vista use EasyBCD to check your boot entries

---

### Post by guidemeintheeyesofblindne on 2008-03-13
Wow that doesn't make any sense to me at all. 

I'm using windows xp home edition and as far as I can tell the latest wbui download right from the wubi website.

---

### Post by ago on 2008-03-13
> **guidemeintheeyesofblindne said:**
> Wow that doesn't make any sense to me at all. 

I'm using windows xp home edition and as far as I can tell the latest wbui download right from the wubi website.

Use this then: [http://www.wubi-installer.org/devel/minefield/Wubi-8.04-alpha-rev451.exe](http://www.wubi-installer.org/devel/minefield/Wubi-8.04-alpha-rev451.exe)
There should be a file C:\boot.ini (might be hidden), make sure you have permissions to edit that file.

---

### Post by guidemeintheeyesofblindne on 2008-03-13
There should be a file C:\boot.ini (might be hidden), make sure you have permissions to edit that file.

Sure. 

How on Earth do I go about doing that?

---

### Post by ago on 2008-03-14
You set windows explorer to show hidden files, you double click on boot.ini, write something to it, try to save, undo the changes.

---

### Post by guidemeintheeyesofblindne on 2008-03-14
You don't explain things very well at all. 

Never mind I'll get help somewhere else.

---

### Post by jmjm on 2008-03-15
Once you have completed downloading Ubuntu, restart your computer with F8 depressed. This will open the boot menu, which will now include a Ubuntu option. Select this and you will be prompted to select a Ubuntu installation option. Do this and Ubuntu will be installed.

Once this is done, subsequent (re)boots will give you the choice of Windows or Ubuntu.

---

### Post by guidemeintheeyesofblindne on 2008-03-15
Thanks. Just tried it. Didn't work. Ubuntu load option was not available after the f6 option {or f10}.

---

### Post by jmjm on 2008-03-15
F8 on booting, not F6 or F10.

What do F6 and F10 do?

---

