---
title: "Having multiple problems with Hardy."
date: 2008-06-27
forum: General Help
---

### Post by billdotson on 2008-06-27
I am having multiple problems with Hardy.  I think that I really shouldn't be having such issues as it is a relatively new install and I haven't been in the system files screwing around. 

About 1 in 3 or 4 times upon booting the system will not boot into gnome.  If I tell it to start gnome it says "starting gnome display manager" or something similar but doesn't do anything.  If I restart gnome it boots into gnome.

Also, sometimes when it boots into gnome the desktop is gone.  The panels and everything like that are there, but the desktop background and everything on the desktop is gone (the files are still in the Desktop folder).  So essentially it is a "background" of the Ubuntu color that is not interactive at all (can't right-click, etc.)  A ctrl-alt-delete seems to fix it in most cases.  I have an 8800GT 512MB PCI-E x16 video card which could be the issue but I have the latest proprietary driver installed and it works with Compiz fusion and the emerald themer fine (unless I try to play games and then some of them crash, mainly Tremulous).

This morning I got a really annoying error, when I tried to boot up Ubuntu it went through the basic stuff but right at the end it said "BUG: soft (some other word I forget; I think power) CPU #1 stalled 11s and just kept repeating that.  There was a different number between each line; one of them was something like 154.something.

Also, when Ubuntu installed some new updates that required a reboot I tried booting the Vista bootloader form GRUB and it just restarts the computer's bootup process.  Before this it worked fine.  I checked the menu.lst entry and it looks fine (Windows Vista Bootloader, chainloader +1, etc.; if it didn't ubuntu wouldn't boot) and fstab.

I really don't think I should be having this many issues having not really changed all that much.

Any help would be appreciated.

---

### Post by Dzenhax on 2008-06-27
I can't give you the answer yet, but let's eliminate the hard ware itself as an issue.  Does the machine dual boot?  If you are dual booting and not having issues in the other OS, then we know that dying hardware is not the issue.

If you aren't dual booting, run a Live OS disk on the system for a few hours (you have to use it so make up work if you don't have any to do) and see if that works fine over a couple of reboots.

If both those tests are sucessful start looking at Ubuntu.  You might also check google and search for your video card and Ubuntu to see if you get any insight there.

---

