---
title: "wireless connection?"
date: 2004-10-28
forum: General Help
---

### Post by fisherdmin on 2004-10-28
I'm test driving Ubuntu with the LiveCD - worked flawlessly on the Latitude 600.  Kudos to the prgramming team!

I can't figure out how to configure the wireless..  I'm accustomed to a GUI inerface, but have dug around trying to configure the wireless hardware.  I could probably activate it if I knew what ithe device was called.  I have run lsmod and modprobe with no real results.

Anybody have suggestions?

Thanks, 

fisherdmin

---

### Post by fisherdmin on 2004-10-29
Update .... I found the GUI interface for configuring the networking (cleverly hidden in plain sight  ;-)  ).

I switched from onboard wireless to a separate Orinoco Silver card, with the same results.  When I run the network config, I do not get a drop down list of available cards, even after I edit the /etc/pcmcia/wireless.opts file to remove the non-start lines and then run /etc/rc.d/init.d/pcmcia restart.

FWIW, I DO see the card during the boot process, listed as an Agere Systems 110 (Orinoco Silver).  However, when I do a modprobe of orinoco and orinoco_cs, then do an lsmod, upon inserting the card in the PCMCIA slot, I get the "BAD" beep, instead of the "GOOD" beep, which I think means wrong driver. 

I'd love to get this to work ....

fisherdmin

---

