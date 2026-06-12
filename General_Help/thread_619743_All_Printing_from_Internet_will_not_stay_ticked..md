---
title: "All Printing from Internet will not stay ticked."
date: 2007-11-21
forum: General Help
---

### Post by feisty_hot_lover on 2007-11-21
Hi, when I tick the "Allow Printing From Internet" in the printer setup GUI and click apply and then close the printer setup GUI and reopen it, the "Allow Printing From Internet" is not checked.  I would like to allow printing over the Internet from specific IP addresses and specific host names.  I would also like to require password.  My printer is a Okidata B4350 LAN PostScript printer.  I have already read this thread: 

[http://ubuntuforums.org/showthread.php?t=56580](http://ubuntuforums.org/showthread.php?t=56580)

That thread is from 2005 so I don't know if it applies to 7.10 or not.  Any help would be appreciated.

---

### Post by kelbizzle on 2007-11-21
I think I've noticed this in one of my customers computers. But I have to double check.

---

### Post by feisty_hot_lover on 2007-11-22
I got it to work.  I made the mistake of not realizing the printer had a built in print server, which means cups does not act as a print server but as a client only.  I simply setup everything in my print server and voila!

---

