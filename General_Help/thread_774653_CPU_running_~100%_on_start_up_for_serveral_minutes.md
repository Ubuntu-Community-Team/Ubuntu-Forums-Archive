---
title: "CPU running ~100% on start up for serveral minutes"
date: 2008-04-29
forum: General Help
---

### Post by guy.murray on 2008-04-29
Hi,
   this started after I printed a document at a hight res setting.

Now every time I log on the system seizes up with the monitor showing around 100% whilst no processes are listed that are causing it. Also the hard disk is constantly reading or writing.

After about 5 minutes it settles down, but happens again when next booting.

Anyone any ideas?

Guy

---

### Post by GCoffee on 2008-04-29
Check your startup sessions, are there any apps there that take up a lot of processing power?

How much ram do you have, what processor?

Could this be your printer doing something?

---

### Post by yaknowwat on 2008-04-29
Sounds like very aggressive tracker settings.

System > Preferences > Searching and Indexing

Take it and adjust it as needed  I suggest going under Performance and throtling it way down

---

### Post by guy.murray on 2008-04-29
Thanks for the prompt replies.

It turned out to be quite simple, there was some stuff still in the printer buffer and the printer wasn't switched on when I next started the computer. 

CUPS must have gone crazy trying to finish the print job!

Clearing the print queue solved it.

Doh.

Guy

---

