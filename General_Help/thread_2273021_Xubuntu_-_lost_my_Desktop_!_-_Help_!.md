---
title: "Xubuntu - lost my Desktop ! - Help !"
date: 2015-04-10
forum: General Help
---

### Post by Tim036 on 2015-04-10
I loaded 12.04 Xubuntu 32 bit onto a very old Thinkpad.  It worked fine.  But it asked me to upgrade to 14.04 lts, about 12 hours plus later it had done, and I populated the Desktop with various useful programs such as the Arduino ISE and Dolphin.

When I woke it up this morning I had none on the items on the Desktop.  It was blank.(well dark).

I got 'File' running and then got Dolphin running and discovered 'Desktop'.  Do all is well...

But it would be a lot better if I could get 'Desktop' back on the screen !

Hope this makes sense.....

Any thoughts would be very much appreciated.

a puzzled,

Tim

---

### Post by kerry_s on 2015-04-10
well where'd ya last see it ? lol, sorry couldn't help myself

so dolphin is a kde/qt program, by any chance you accidentally install kde ? try logging out & making sure xubuntu is the session your using.

---

### Post by The Cog on 2015-04-10
It is possible that the desktop settings utility has changed over the intervening time, and the old settings config you have is causing issues. First off, I would call up the settings from the menu (I think in 14.04 they were not actually in the menu with other programs, but there was a settings icon embedded in the bottom of the menu panel). Then fiddle with some of the desttop settings there and see if this corrects things.

---

### Post by Tim036 on 2015-04-10
Files is good and has neat features such as remove gadget for SD cards and DVD discs etc,  but Dolphin has neat features too.  So I use both.

Many thanks for responding, greatly appreciated.  As Desktop has escaped.. I use Files to find it and I open a large Window and proceed from there, but there ought to be a neater way...

and

I found the Settings and juggled a bit but so far didn't fix it.

Tim

---

### Post by The Cog on 2015-04-10
You could try renaming the folder .config/xfce4 (.config is a hidden folder in your home directory) which holds all your xfce4 settings. then log out and back in again to get the default settings. If that fails, rename the new ./config/xfce4 and rename your original back. I find that I have to lose all my custom settings occasionally after an upgrade, presumably because the new version has slightly different settings parameters.

---

