---
title: "k9copy closing when open dvd..."
date: 2007-09-17
forum: General Help
---

### Post by Mia_tech on 2007-09-17
I'm trying to backup some of my dvds and when I hit the open button on the menu it closes automatically....does anybody knows why?

thanks in advance

---

### Post by becatlibra on 2007-09-17
What do you mean "when you hit the open button on the menu?"  You mean to start the program?

how was it installed?  using add/remove programs?  if not maybe you are missing some dependencies?

Benjamin

---

### Post by Mia_tech on 2007-09-17
I installed it using the synaptic package manager, once the program is opened there's a open folder button that is spoused to open the content of the dvd, when I hit that button it automatically closes, giving me some error...........I'd have to replicate the error and post the logs here

---

### Post by becatlibra on 2007-09-17
yes - logs are good :D

---

### Post by Mia_tech on 2007-09-18
> **becatlibra said:**
> yes - logs are good :D

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1240992048 (LWP 12857)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0x080678b6 in ?? ()
#7  0x081cdef8 in ?? ()
#8  0x00000001 in ?? ()
#9  0xbf9374b0 in ?? ()
#10 0x00000000 in ?? ()

---

### Post by gustysoft on 2007-11-14
Hi:
My name is Gustavo and I'd got the same problem. So I did that: I chek out the dependencies (check in the forum: mplayer, memcoder, dvdauthor and
Well chek out this: I had installed the mplayer gui pack, so I uninstalled and installed the mplayer pack. So my problem is resolved.
I hope u understand what I'm saying, English isn't my natural language. So I'm learning.
Bye.
Gustavo

---

