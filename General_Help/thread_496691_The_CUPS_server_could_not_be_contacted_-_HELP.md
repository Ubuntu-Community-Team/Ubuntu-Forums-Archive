---
title: "The CUPS server could not be contacted - HELP"
date: 2007-07-09
forum: General Help
---

### Post by SiriusB on 2007-07-09
Hi there

OK, really, really, *really* aggrivating problem with CUPS!

Up until yesterday CUPS was working just fine on my Feisty Fawn machine.  In fact, I was successfully sending print jobs to another Ubuntu machine downstairs which was connected to my Brother DCP-115C.

However.  Yesterday afternoon I decided to play with Samba as there are two Windows machines in the house and I wanted them to be able to send print jobs to the Print Server.

So, having been thoroughly vexed by Samba I decided to use SWAT.  So installed that, had a little tinker but didn't really achieve anything.

I then decided to check something about the installed printer so went to System > Admin > Printing and I get a rather lovely "The CUPS server could not be contacted" message.

Me:  Ok

So I tried restarting the CUPS service

```

sudo /etc/init.d/cupsys restart

```

Everything appeared to be in order.  Try going to the Printing dialog and again, I am faced with the same error.

I have, numerous times, uninstalled, purged and reinstalled Samba, SWAT and CUPS in just about every combination possible.  Same error every time.

The CUPS service is running but it appears it doesn't want to do anything!

I have tried all sorts of stuff and I am at a complete loss now.  I am THIS close to doing a reinstall.  I just really rather wish I didn't as it would be a major pain in the rear.

If anyone has any help, advice or magic pointy sticks I can poke Feisty with then I will be very grateful!

---

### Post by James Little on 2007-08-23
I have exactly the same problem, and I also had a play with Samba and Swat recently. The cupsys service is running and restarts OK, I've uninstalled, reinstalled etc. so I have a fresh cups config file but still no luck via System > Administration > Printers - just the message "The CUPS server could not be contacted."

Anyone got any ideas?

---

