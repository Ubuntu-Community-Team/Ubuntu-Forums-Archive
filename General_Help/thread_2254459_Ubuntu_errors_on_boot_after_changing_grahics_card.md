---
title: "Ubuntu errors on boot after changing grahics card"
date: 2014-11-27
forum: General Help
---

### Post by george-r-nelson on 2014-11-27
I have a problem after I changed my graphics card on Ububtu 14.04. The system rebooted successfully but was using a standard graphics driver for the new card. I updated the driver via software updates and it installed correctly. However, when I rebooted the machine, the boot fails with a somewhat garbled screen of messages with the Ubuntu boot progress indicator still in the centre of the screen. I've tried running a restore on the system but this ends up with a black screen apart from the cursor indicator in the top left.

I have tried various approaches to repairing the system, including running a LiveCD on the system and installing a new copy on a separate partition. In both cases, my Ethernet card was not detected so could not download the repair S/W. If I run lshw -C Network it reports that the network is unclaimed but lspci does show the Ethernet card. I'm wondering if this may be a source of the boot problem.

Thanks,

George

---

### Post by irv on 2014-11-27
If you can boot with a liveCD, even thought you don't have a working network you can still backup your files if you have to. After that I would pull the new graphics card out and then put it back in again making sure it is seated good in the motherboard. Then go into the BIOS and make sure everything is set right there. Then try the install again. I'm thinking it might be a conflict of IRQ between the graphics card and network card. Remember I'm just guessing. What makes me say this is because your network was working before you put in your new graphics card.

---

### Post by george-r-nelson on 2014-11-27
I've tried all you suggested but still no luck. Ubuntu still refuses to recognise my ethernet card. I can certainly access my files on the original system (I have a second version of Ubuntu on the system) and I have a 2TB drive I can add to backup my files but I'm still dead in the water if I can't get Ubuntu to recognise the network. Thanks for the help though.

---

### Post by irv on 2014-11-27
Can you get the network card to work if you put the old graphics card back in? I take it it was working before you changed it out?

---

### Post by george-r-nelson on 2014-11-27
No, the network card still doesn't work. I've even tried it in a different slot. At the moment I have both cards in. I did some more investigation with my original system. As I said, I get the Ubuntu boot screen and then a screenful or error messages although the boot progress indicator is still showing. Finally managed to get the error - it is multiple repeats of the following:

/lib/udev/socket:@/org/freedesktop/hal/udev_event' socket:@/org/freedesktop/hal/udev_event': No such file or directory

From Google, it seems that hal has been dropped (my original installation was quite a few years ago). However, since I don't get past the boot splash screen I can't see any way to remove it.

---

### Post by george-r-nelson on 2014-11-29
I've still not made any progress trying to repair my system although I now have a second Ubuntu install that does (almost) work - just does not recognise my Ethernet H/W. However, it does let me look at the original system but I have no idea what logs I should examine to see if I can determine what the original problem was that might help me repair the problem. An alternative would be to do a new install on a second hard drive but then I'd need to find out why it is not recognising the Ethernet H/W. Would be grateful if anybody could point me at logs to look at or how to fix the Ethernet recognition issue.

Thanks,

George

---

