---
title: "beagle pdfinfo"
date: 2005-07-17
forum: General Help
---

### Post by art on 2005-07-17
Hi forum
The problem is the following. I compiled 2.6.12 kernel with inotify patch, installed beagle, and it seemed to be allright. But now I notice that there are just tens if not hundreds of pdfinfo, pdftotext processes and also mono processes running in tree, and CPU is going up to 100%. Has this been noticed by someone, or I am doing smth wrong, or this is normal (which I doubt)? The beagle is 0.0.11.

---

### Post by varunus on 2005-07-17
I know that beagle spawns tons of mono processes to index your data in the background, but it shouldn't push CPU up to 100% unless you have the "BEAGLE_EXERCISE_THE_DOG" environment variable set.  For me, it doesn't push it up that much (at most 10% i've seen) but I don't have pdfinfo.  It could be a possible bug, Beagle is in alpha (and a new version was just recently released, but isn't in Ubuntu yet).

---

### Post by manicka on 2005-07-17
The beagle wiki advises not using inotify with hoary

[http://beaglewiki.org/Ubuntu_Installation](http://beaglewiki.org/Ubuntu_Installation)

---

### Post by art on 2005-07-18
Well I thoght the wiki is not recommending inotify because there is no official inotify kernel for ubuntu, and there are for other ditros. Anyway another problem is even if I don't use the inotify kernel, whenever I log out and log back in, the files beagle was finding in the previous session don't get found immediately, but it needs some time, after which it finds them again. Is this the same with you guys? I am running beagle-0.0.12. I have set beagled and best to start in each session.

---

### Post by manicka on 2005-07-18
I haven't bbeen able to get around this issue of the file cache resetting at each login either. For now I've turned it off and just use beagle for indexing all the other stuff and using gnome search for files. 

Hopefully it will be working properly by breezy

---

### Post by art on 2005-07-18
So I excluded couple of directories from being indexed, and now CPU never goes that high. I am using inotify patched kernel. 
Thank you guys!

---

### Post by damonw5 on 2005-07-18
[QUOTE=art]So I excluded couple of directories from being indexed, and now CPU never goes that high. I am using inotify patched kernel. 
Thank you guys![/QUOTE]
 art,

Could you tell us which directories you excluded in case someone has a similar problem?

Thanks!

---

### Post by art on 2005-07-18
Sure. I excluded a madwifi (driver for Atheros WiFi) directory, which seemed to take too much time, I also have ROOT installed on my lappy, which is a a framework for C++. Also Mail, both local and IMAP. After that it works like a charm. Even the issue of not having the index of the previous session dissapeared. Beagle-0.0.12. Kernel 2.6.12-inotify patched.

---

