---
title: "Slow start 16.04 AMD64"
date: 2017-09-27
forum: General Help
---

### Post by Robbyx on 2017-09-27
Could someone please look at the attached file arising from 

systemd-analyze plot > test2.svg

The slowest part is near  the end.

I would appreciate some help as to how to cut down the login time. Incidentally now that I am using the Xanmod kernel it is much faster than on vanilla gnome but I would like to optimise the startup  further.

Robin

---

### Post by Robbyx on 2017-10-01
As no one has responded, any chance of a reply?

---

### Post by jeremy31 on 2017-10-01
Try ```
systemd-analyze blame > blame.txt
```
Post the contents of blame.txt
I never cared for the graph

---

### Post by Robbyx on 2017-10-01
Thank you for your request.  I agree the text version is much better. I have recently changed my kernel to XanMod and it has helped a lot, including speeding up the boot process.  If you can see a way of making the startup process even quicker I would be grateful.

Robin

---

