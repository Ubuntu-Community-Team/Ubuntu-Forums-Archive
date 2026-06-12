---
title: "Ubuntu wont boot from External HDD (grub menu shows)"
date: 2013-12-17
forum: General Help
---

### Post by tlino on 2013-12-17
[COLOR=#000000][FONT=Arial]Recently installed Ubuntu 13.10 on an EXT HDD I bought. The EXT HDD is called: "WD My Passport" and it's got a storage size of 500GB.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I installed it from a USB drive on my desktop, installing it to a 150GB size partition on my EXT HDD.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]After installing, I rebooted my desktop, and it worked! After installing a few programs (playonlinux, ubuntu tweak tool, etc.), I also changed the graphics driver to fglrx-updates for my ATI-Radeon HD 7770 card.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So I decided to reboot after I did that, but surprisingly, when I selected "Ubuntu" in the GRUB menu, nothing happened! It went to a blank purple screen.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I figured maybe my EXT HDD partition was corrupt, so I tested it on my Laptop to make sure. For some reason, it boots perfectly on my Laptop. I have no idea why.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]It doesn't boot on my Desktop. So I'm assuming there is some BIOS option I need to enable/disable to get Ubuntu 13.10 working on my Desktop?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I bought the EXT HDD so I could easily bring my Linux OS anywhere I went, however I don't know why it won't boot from my Desktop.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm using an MSI Motherboard. Can anyone tell me what BIOS settings I need to set in order to get it booting?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]It's weird, it worked the first time I booted it, but then when I reset it, it didn't work on my Desktop. Works perfectly fine on my Laptop. Rebooted it multiple times too on my Laptop and it works, but not my desktop.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Help would be much appreciated.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**TLDR;** Ubuntu installed on my External Harddrive "WD My Passport 500GB", wont boot on desktop, but boots on laptop. Bios settings needed to get it working?[/FONT][/COLOR]

---

### Post by spencer the great on 2013-12-17
It sounds more like a graphics problem.  Can you bring up a TTY on the blank purple screen? (CTRL-ALT-F1 - CTRL-ALT-F6)

---

### Post by Bucky Ball on 2013-12-17
Welcome. Two words:

fglrx-updates

That is your problem I would say. Something about that driver and the hardware on that machine is not working. Boot the hard drive from another machine, get rid of that driver from Additional Drivers and I don't doubt it will boot again. Let us know. (The fglrx-updates driver is not always or generally the best option.) 

There is nothing corrupt about your hard drive. It is working fine everywhere else.

* You can also try this: when you get to the menu list, choose your Ubuntu line and hit 'e' to edit it. Find the line that ends in 'quiet splash' or either one of those words. At the end of the line, after one space, add 'nomodset' (no apostrophes). Follow instructions at bottom of screen to save and proceed. 

This will ignore the fglrx driver and should get you past the purple screen. The purple screen after boot pretty much says 'graphics problem' in all but rare cases.

---

### Post by tlino on 2013-12-18
It seems that was the problem.
I switched it to the default driver in the "Additional Drivers" menu on a machine that could boot it, and now it boots on Desktop.
However, what if I wanted to install AMD Radeon 7770HD drivers, it's just going to crash again.

What would I do?

---

### Post by Bucky Ball on 2013-12-18
Don't install the 'fglrx-updates'. Just go the regular in Additional Drivers. See how that goes. If it breaks you now know how to fix it.

Word of advice though: If you intend pursuing getting the fglrx driver working, please start another thread in ***Multimedia & Video*** regarding this with a descriptive title and a link back to this thread perhaps (so people can see what you've already tried). 

The title of this thread now has nothing to do with what you have discovered your issue to be and the problem has headed in another direction.

Post a link to the new thread back here. Good luck.

---

