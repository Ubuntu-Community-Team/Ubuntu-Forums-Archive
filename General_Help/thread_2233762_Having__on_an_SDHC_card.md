---
title: "Having / on an SDHC card"
date: 2014-07-10
forum: General Help
---

### Post by t0p on 2014-07-10
I have an EeePC; one of the oldies with a 4 GB SSD.  It also has a SD card reader, so when I installed lubuntu on it I put /home on a 8 GB SDHC and everything else on the 4 GB SSD.

Unfortunately the SSD is full, I can't do updates without deleting applications or such stuff from / .  So, I'm thinking maybe I could reinstall, putting /home on the SSD and / on the larger SDHC.  Is this possible?  I know it'll slooow everything down, but I think I could cope with that.  But I don't want to attempt the reinstallation if it won't work.  I hate installing.

Cheers.

---

### Post by ajgreeny on 2014-07-10
Does that machine have the ability to boot from an SDHC card in an integral card reader?  It may be possible, but I know some machines will not do so.  Do you have another SDHC card on which you could put a live Ubuntu system to see if the machine will boot from that; if it will you may be in luck.

PS: A quick search shows that it can boot from those cards [http://www.ehow.co.uk/how_6953228_boot-eee-pc-sd-slot.html](http://www.ehow.co.uk/how_6953228_boot-eee-pc-sd-slot.html) so why not try it?  Installing is such a quick job with the *ubuntu family.

---

### Post by t0p on 2014-07-11
Thanks for the reply ajgreeny.  I know I can boot a live session from the card reader.  What I want to know is if it's possible to have / permanently on the card and /home on the SSD.  I've posted here because I am hoping that someone has already tried this and can say yes or no.  I'm not keen on just giving it a go as installing onto an EeePC is very slow and taxing on the patience.

I think I'm going to wait a bit longer, see if anyone can answer my question and do some more googling.

Cheers.

---

### Post by ajgreeny on 2014-07-11
If both disks are available and mounted at boot by the system I see no good reason why it would not work as you want to.  I have no experience of that particular Eeepc, but I do think I remember hearing that the 4GB SSD used in them was a poor, slow speed one, so your setup suggestion may not be that much different speed wise from the way you have it now.

You could consider using clonezilla to clone your current OS partition from the SSD and restore it to the SD card, but I have no real knowledge of clonezilla in use, and it may be just as quick to reinstall using the something else option when you install from the USB.

---

