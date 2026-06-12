---
title: "[SOLVED] Apt-get, Synaptic, and Add/remove programs not working - PLEASE HELP!"
date: 2008-01-04
forum: General Help
---

### Post by intimaAcE on 2008-01-04
Hi, whenever I try to use apt-get, synaptic or the add/remove programs program, I get an error saying

"[B]E: Archive directory /var/cache/apt/archives/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Unable to lock the download directory[/B]"

I'm on a laptop (EEE pc) with only **4GB of storage**, and at the reccomendation of someone one the eeeuser.com forums **I deleted the contents of this directory**, which was taking up about **600mbs of space**. He and I thought them to be just cache files that could be re-downloaded, but now I always get this error. I realise this is 100% my fault, and was probably a stupid newbie move, but I really want to get this working again.

Obviously my system is pretty much crippled without the ability to install/remove any programs, so **please help!**

---

### Post by rubicon on 2008-01-04
Um. Have you tried to 'sudo mkdir /var/cache/apt/archives/partial' ?

---

### Post by forestpixie on 2008-01-04
found a few things that could help

```
http://www.uboontu.com/results.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=E%3A+Archive+directory+%2Fvar%2Fcache%2Fapt%2Farchives%2Fpartial+is+missing.#1351
```

this one in particular looks quite handy, post 7 onwards - [http://ubuntuforums.org/showthread.php?t=94045](http://ubuntuforums.org/showthread.php?t=94045)

Edit - snap :) - once he's read the thread, although there are a couple of other things added

---

### Post by intimaAcE on 2008-01-04
Hehe, thanks very much for the quick replies guys, but as soon as I posted that I realised what the problem was. I just created the directory it was complaining about as rubicon suggested and all is now well.

Well I feel like an idiot.

---

### Post by forestpixie on 2008-01-04
could you mark thread then :)

---

