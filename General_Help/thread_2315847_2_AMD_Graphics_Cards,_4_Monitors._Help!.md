---
title: "2 AMD Graphics Cards, 4 Monitors. Help!"
date: 2016-03-03
forum: General Help
---

### Post by hawk16 on 2016-03-03
I have 2 Asus R9 280X

I am trying to run 2 monitors on each of the cards, and the first card is recognized by fglrx (proprietary) no issues and those 2 monitors work. The other 2 monitors connected to the second card are not recognized whatsoever and no matter what I click in catalyst I cannot get those 2 monitors recognized. 

Any ideas or suggestions?

---

### Post by QIII on 2016-03-03
Hello!

When you installed fglrx, did you do

```
sudo amdconfig --adapter=all --initial
```

to make sure *both* cards were initialized?

---

### Post by hawk16 on 2016-03-03
> **QIII said:**
> Hello!

When you installed fglrx, did you do

```
sudo amdconfig --adapter=all --initial
```

to make sure *both* cards were initialized?

Yes I did. I even checked the xorg.conf to make sure, but when I rebooted the xorg.conf reverted back to just the single card. Even editing the xorg.conf and rebooting it changes on it's own.

---

