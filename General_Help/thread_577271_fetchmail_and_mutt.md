---
title: "fetchmail and mutt"
date: 2007-10-16
forum: General Help
---

### Post by go_beep_yourself on 2007-10-16
How can I change the location of where fetchmail downloads emails to the mbox file? Each time I start mutt, it asks me if I want to create a Mail directory in my home directory. Is there where the mbox file usually goes? My mbox file is in my home directory. What is the Mail directory that mutt keeps creating in my home directory for? What is a mail spool? I searched google for a definition and wikipedia but did not find anything.

---

### Post by andrew.46 on 2007-11-11
Hi,

 I am not sure if I can help with *all* of your requests:

> **go_beep_yourself said:**
> How can I change the location of where fetchmail downloads emails to the mbox file? Each time I start mutt, it asks me if I want to create a Mail directory in my home directory. Is there where the mbox file usually goes? My mbox file is in my home directory. What is the Mail directory that mutt keeps creating in my home directory for? What is a mail spool? I searched google for a definition and wikipedia but did not find anything.

but could I suggest you read theough a walkthrough i wrote a while ago on using mutt:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

 I will admit that I use getmail rather than fetchmail as the setup is much less of a hassle, perhaps you could look into that?

               Andrew

PS Have a look in your ~/.muttrc for the directory you have named "set spoolfile= ...." and make sure it exists.

---

