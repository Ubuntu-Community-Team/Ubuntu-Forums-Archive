---
title: "I'm not getting asked for passphrase for encrypted partition anymore"
date: 2015-07-28
forum: General Help
---

### Post by wudu2 on 2015-07-28
Hi,

I'm using xubuntu 14.04. I have an external HDD with an encrypted partition. Until recently there was a popup window after clicking on the partition in Thunar for entering the passphrase with options to "Forget password immediately", "Remember password until you logout" and "Remember forever". I must have accidentally clicked "Remember forever" at some point. So now theres no popup window anymore and I can't change these setting and the partition gets automatically mounted. So the passphrase has to be stored somewhere. How can I get back the old behavior (popup windows asking for passphrase)?

---

### Post by veddox on 2015-07-28
My first guess would be to check in your key managing program (Seahorse on vanilla Ubuntu, not sure what Xubuntu uses). If you can find an entry there for you HDD, there's sure to be a way to get rid of it.

---

### Post by wudu2 on 2015-07-28
> **veddox said:**
> My first guess would be to check in your key managing program (Seahorse on vanilla Ubuntu, not sure what Xubuntu uses). If you can find an entry there for you HDD, there's sure to be a way to get rid of it.

WOW, many thanks. There wasn't anything like that installed. But after installing seahorse it just was there. Deleted the entry for that partition and there it was again, the popup asking for passphrase like it was before.

This or something similar should be installed by default in Xubuntu as well (there's an option you can't change back anymore without knowing which additional software to install, OMG).

---

### Post by veddox on 2015-07-28
Glad to be of service :-)

Seahorse is actually just a graphical front-end for the commandline utility gpg, which is also installed on Xubuntu by default. So if you're a terminal junkie, you *could* have done it with that, though I find gpg rather difficult to use (despite being quite at home in terminal).

---

### Post by wudu2 on 2015-07-28
Ah, OK. I don't have a problem with the terminal... But still bad in my opinion to have a graphical option for something which then prevents to get to that graphical option again...

---

### Post by veddox on 2015-07-29
I agree. I'm surprised Xubuntu doesn't have a graphical key management program installed. Consider submitting a bug report.

---

