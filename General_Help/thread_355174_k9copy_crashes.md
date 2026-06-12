---
title: "k9copy crashes"
date: 2007-02-06
forum: General Help
---

### Post by joriad on 2007-02-06
I have been having some problems copy dvds with k9copy. It seems that it will copy one dvd fine but crashes when copying a different dvd. I thought at first it was a dirty or scratched dvd but this one is brand new and i have actually had success copy dvds that were very severely scratched. What I get is: This application k9copy (k9copy) crashed and caused the signal 11 (SIGSEGV).

Backtrace

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1240193360 (LWP 5036)]
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
#6  0xb5c8b250 in ?? ()
#7  0xb63bbfb5 in ?? () from /usr/lib/libdvdread.so.3
#8  0x0821b0e8 in ?? ()
#9  0x000002cd in ?? ()
#10 0x00000000 in ?? ()

I am using k9copy 1.1.0 (using KDE 3.5.5)
Does anyone have any ideas on this?
Thanks for any help in advance.

---

### Post by jmervyn on 2007-05-05
You aren't the only one, but I'm sorry that I have nothing constructive to add.  I am now encountering identical problems with Feisty Fawn, but that's before the interface ever opens.  There's at least a couple of entries on Google about the same sort of issue; hopefully someone can lend a hand.

---

### Post by cutlerite on 2007-11-24
I'm having this issue in Gutsy.  I read somewhere that you need to delete a config file, however I can't find it.

---

