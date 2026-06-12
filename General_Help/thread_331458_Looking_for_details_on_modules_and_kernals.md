---
title: "Looking for details on modules and kernals"
date: 2007-01-04
forum: General Help
---

### Post by greatgoo on 2007-01-04
Almost kind of a cross post but not really.  I am trying to understand how the system sees hardware and configures for it.  Also posted in the Video forum ...

I am working on getting a ATI TV card to work in my Linux Box. I have read the various postings I could find here, tried the various fixes, crashed the box four times, rebuilt it three times and saved it the last time. I am getting better, but still have a lot to learn.

When I look at the system log, either through Gnome or using dmesg, I see the card is identified as a Connexant based card, but it is not recognised. There is then a list of common cards one could use use with the insmod command, card=#. The man page for insmod says modprobe is better. TV Now and the v4l project talk about patching the module ... on and on and on.

First what I am looking for is a better understanding of hardware detection. How the kernal decides what to do when a piece of hardware is found. Anyone got a link to that?

Next I would like to better understand the module process. How about a link to that.

Finally, when I tried the insmod command or the modprobe command to set the card number to 4, no module is found. Playing with the various module possibilities for Connexant, none of those modules are found, hence my above request for kernal knowledge. Has anyone got any ideas on that?

David Davis
Toledo, OR 97391
Reply With Quote

---

