---
title: "Black Screen"
date: 2015-02-28
forum: General Help
---

### Post by Y^2om&amp;#7sgP on 2015-02-28
Hopefully this is the correct area, if not please accept my apologies now.

I'm runing Xubuntu 14.04.02 64 bit on a HP desktop.  Installed yesterday as I'd added so much junk on my previous install that it just seemed easier to start fresh.
Install went OK, later in the day I had an alert of an update.
This installed kernel 3.16.0-31-generic, again all appeared OK, reboot at the end, everything working.
Now, after switching off overnight, the PC starts, displays the Xubuntu screen, then goes blank, nothing at all.
It I press ctrl-alt-F3, then ctrl-alt-F1 I get a text login and can login with my username and password, then startx to get a desktop, but trying a reboot or shutdown I have to enter my sudo password.
Rebooting gets the same problem.
Can anyone assist please in getting back to a working system, without another rebuild?

Thanks guys

---

### Post by v3.xx on 2015-02-28
I wonder if nomodeset would do any good.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by sandyd on 2015-02-28
> **hattpa said:**
> Hopefully this is the correct area, if not please accept my apologies now.

I'm runing Xubuntu 14.04.02 64 bit on a HP desktop.  Installed yesterday as I'd added so much junk on my previous install that it just seemed easier to start fresh.
Install went OK, later in the day I had an alert of an update.
This installed kernel 3.16.0-31-generic, again all appeared OK, reboot at the end, everything working.
Now, after switching off overnight, the PC starts, displays the Xubuntu screen, then goes blank, nothing at all.
It I press ctrl-alt-F3, then ctrl-alt-F1 I get a text login and can login with my username and password, then startx to get a desktop, but trying a reboot or shutdown I have to enter my sudo password.
Rebooting gets the same problem.
Can anyone assist please in getting back to a working system, without another rebuild?

Thanks guys
Hi, what video card do you have?

---

### Post by Y^2om&amp;#7sgP on 2015-03-18
Well, after giving up (shouldn't have) I re-installed win7. It installed OK, but after re-booting, I got a couple of lines for text on a black screen.
I then found thet if I removed my external USB HDD, everything booted normally.
Soooo, back home to Xubuntu.  External drive backed up and re-formatted.  Now everything works perfectly again.

Seems that one of the updates had put 'something' (maybe a component of grub?) onto the USB drive, which caused the whole machine to fail in booting.

Thank you to all who made suggestions, but as usual, the simplest answer was correct.

Oh, and sorry for the trouble I must have caused :oops:

---

