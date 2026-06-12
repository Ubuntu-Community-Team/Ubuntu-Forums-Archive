---
title: "How reliable is hdparm?"
date: 2008-01-22
forum: General Help
---

### Post by skymera on 2008-01-22
i find hdparm to be somewhat, very unreliable and unaccurae.

for instance this:

```
 scott@scott-desktop:~$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:   74 MB in  3.10 seconds =  23.91 MB/sec
scott@scott-desktop:~$ sudo hdparm -t /dev/sdb

```

thats low for my drive.

yet if i do this

```
 scott@scott-desktop:~$ sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   2246 MB in  2.00 seconds = 1123.42 MB/sec
 Timing buffered disk reads:  240 MB in  3.01 seconds =  79.61 MB/sec
scott@scott-desktop:~$ 

```

much much higher, yet it still same test?

---

