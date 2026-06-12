---
title: "100% disk usage"
date: 2014-06-05
forum: General Help
---

### Post by zcastagna84 on 2014-06-05
Hey all, so I had openSUSE on my thinkpad and then the other day I decided to use Ubuntu. I booted to a live disk and proceeded to install at which point it asked if I wanted to replace the openSUSE install with Ubuntu. I did that and now I've got a completely used disk that shouldn't be.. I put a picture below. Hopefully something can be done through GParted. Thanks in advance for the help!

[ATTACH=CONFIG]253740[/ATTACH]

---

### Post by sudodus on 2014-06-05
It is lvm. Is it encrypted too? In that case maybe it only looks completely used, but when you boot into it there will be space.

Can you boot into Ubuntu?

---

### Post by zcastagna84 on 2014-06-05
I dont think I encrytped it. At any rate I just reinstalled and told it to erase the disk and create new partitons and it looks good now. Thanks!

---

