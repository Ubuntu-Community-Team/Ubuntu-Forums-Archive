---
title: "Feel dumb for asking this but..."
date: 2007-06-26
forum: General Help
---

### Post by cyanidearsenic on 2007-06-26
I requested a live Cd a couple weeks ago, got it today and no matter what I do I can't get my computer to boot from the disk.  I tried both of our disk drives and restarted multiple times but all I keep getting is a browser that tells me about Ubuntu and to reboot my computer to use the demo.  So I reboot and it does the same thing again.
I just want to see if I like Ubuntu, I don't want anything installed.
So, how do I boot the live CD without messing up (or overwriting) the current OS?

---

### Post by mikewhatever on 2007-06-26
Change the boot order in the BIOS. Make sure that CDROM is before the HDD.

---

### Post by Yoooder on 2007-06-26
To better explain the previous response:

Here's what to try: Right after you turn on your machine, keep your eye's peeled for a message that says something to the effect of "Press F1 to enter setup, Press F2 to Select Boot Device"  The message should show up within a few seconds of powering on, and if you see anything related to Windows it's too late (just hit the Reset button to try again).

If the message appears do what it says (either option will work for your needs). If you don't see a message then try tapping Esc, F1, F2, and F12 (all separately, these are the most common keys for Setup/Boot options).

If you get into Boot Options: it should be a fairly short list consisting of things like "boot from first hard drive, boot from CD, boot from USB drive" -- make sure your Ubuntu DVD is in your drive, and select "Boot From CD"

If you get into Setup, there could be half a dozen different menus. Firstly, be careful--this is where the machine's most basic settigns are configured -- so don't play with things you don't understand. Look for a "Boot Order" or "Boot Options" screen, and when you find it make sure that "Boot from CD" is above "Boot from first hard drive" (these are all paraphrasing, each machine's Setup is a bit different).

Now, your computer should boot from the DVD, and present you with a menu to Start/Install Ubuntu or do a variety of other tasks. Choose "Start/Install" (the 1st choice) and let Ubuntu load. You will soon see a fully functional desktop, this is the LiveCD :-)  Enjoy

---

