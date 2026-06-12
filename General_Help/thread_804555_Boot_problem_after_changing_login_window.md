---
title: "Boot problem after changing login window"
date: 2008-05-23
forum: General Help
---

### Post by klaasvg on 2008-05-23
Hello gurus,

I really have a nasty problem with my fresh Ubuntu-installation, and i am still eager to keep my PC free of Microsoft-stuff so wanna give it another chance...

My installation worked normally until I changed my login window to "Human List" because I like to be able to select a user from a list.
The next time I tried to boot up, it was hanging before reaching the login screen, leaving the creen showing a montir-message (cannot display this video mode). Pressing Ctrl-Alt-F1 showed some messages with the last one:
"kinit: No resume image, doing normal boot..."
and then it was frozen without any error message :(

So I started from the Grub-menu and entered the Recorvery mode to repair the XWindows (or something like that), I was able to boot normally from the Grub=menu even choosing Generic boot!!! 
SO i reset the original login window to Human, but the problem still exist. I can only boot from the Grub menu, not in the normal way.

There are no error messages so i have very little straws to clutch at... but lease is this a known problem and is there a workaround :confused::confused:

Hope for some help...
grtz Klaas

---

### Post by itix on 2008-05-24
So you get to the desktop after doing the recovery mode thingy?

If you can tell exactly where the problem ocurr, we should be able to solve the problem. 

Booting of grub is the normal way to boot, it's just that you never see the boot menu. I suspect that one of your entries might be broken. That's why I need to establish where the problem is.

---

### Post by klaasvg on 2008-06-20
Hello,
I have waited a few weeks to get a better view on the problem.
The problem still exists but is not completely reproducable.

Many times, when booting the system appears frozen and the harddisk indicator on the PC keeps burning. I discovered that when I press Esc, the indicator goes off and the boot process continues normally.

But sometimes, this does not work. Then I have to reboot and enter the Grub menu and select the first entry (so in fact I boot normally, only using the Grub menu). This always seems to work.

But iti s very strange behaviour and I am afraid that something is broken. I man not sure whether this is really related to the changed login windiw, which I already changed back to the default...

Any ideas?
TIA, Klaus

---

