---
title: "Ubuntu 16.04 generic driver fails for Epson XP-635"
date: 2016-06-30
forum: General Help
---

### Post by Hlass on 2016-06-30
Just got computer back from shop who installed Ubuntu 16.04.  Asked them to install my new Epson XP-635 all in one printer but they couldn't do it as they said "printer is incompatible - generic driver attempted but fails"  
Please can anyone give me and guide me with simple instructions on how to install my new printer?  I cannot believe that the 16.04 version does not support this printer.

---

### Post by howefield on 2016-06-30
Is the "shop" linux friendly, by that I mean are they knowledgeable about it ? 

Bad news is at first glance it appears they may be right, I don't see a driver for this printer on the Epson website, and there are a few threads in these forums with the same problem.

---

### Post by Hlass on 2016-06-30
Thanks for reply.  Yes, shop seems ok with linux.  Generic drivers to be found at  [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)    Haven't installed these yet as I'm unsure which files to download.  (I do know I've a 32 bit)  Can you throw any more light?

I remember somewhere something about installing cups?  Would this help?

---

### Post by howefield on 2016-06-30
> **Hlass said:**
> Thanks for reply.  Yes, shop seems ok with linux.  Generic drivers to be found at  [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)    Haven't installed these yet as I'm unsure which files to download.  (I do know I've a 32 bit)  Can you throw any more light?

Yes, I know where the Epson driver download page is, but couldn't find drivers for your model when I looked. If you have found drivers you would need to download the 32 bit .deb file.

> I remember somewhere something about installing cups?  Would this help?

Cups should already be installed. Check by going to localhost:631 in your web browser.

---

