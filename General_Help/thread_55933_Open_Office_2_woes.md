---
title: "Open Office 2 woes"
date: 2005-08-10
forum: General Help
---

### Post by Zotova on 2005-08-10
I have recently being using the xp version of open office 2 - (I thought I'd try and get rid of MS Office). 

Anyhow I created two documents in the linux version of open office 2 (the one currently available from ubuntu's apt-get). I then opened the two documents within the xp version of open office 2 yesterday (made some changes then saved). 

Today however when I try to open the documents in the linux version it crashes writer. The documents appear to load but then the open office window goes grey, eventually followed by a message saying the program has crashed.

Now I was under the impression that the open office format was supposed to be universal and should work if I open the document on linux, windows, mac, whatever.

The only sort of theory I have is would it be the version on xp is a newer beta and is saving the files in a new way? Hence the older version on ubuntu can't read them?

Just to clarify, when I save a document in linux and open it in linux it works fine, it also loads fine in xp. But when I edit a document in xp or create a new document in xp the linux open office 2 will not read it.

Open Office 2 Ubuntu: 1.9.79.2
Open Office 2 XP: 1.9.m122

Thanks for any help or suggestions.

---

### Post by Zotova on 2005-08-10
Well... I uninstalled all the openoffice related packages with apt-get and then got a debian version of the latest openoffice2 beta. I installed this and got a few errors but everything works fine. (Just incase anyone in the future has the same problem I was having previously).

The errors which I experienced were basically all related to libc6 not being the version openoffice2 apparently requires - the one in ubuntu is version 20 if I remember correctly and the one which is required is version 21. If anyone knows how to fix this I'd be greatful (there is no option to upgrade by using apt-get). Open office2 does work perfectly (so far!) with the current version of libc6 however.

---

