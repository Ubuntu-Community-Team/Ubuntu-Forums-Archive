---
title: "force resolution Ubuntu 12.04"
date: 2014-09-27
forum: General Help
---

### Post by wadie on 2014-09-27
Hi,

I've just installed Ubuntu 12.04 and I'm using Intel Graphics. I can find my monitor resolution in the settings so I want to add it using terminal.
I followed the instructions here
[https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions)

I keep getting "xrandr: Failed to get size of gamma for output default"

How can I get it to work?

---

### Post by mörgæs on 2014-09-28
How does it work in 14.04?

---

### Post by wadie on 2014-09-28
When I try to upgrade to 14.04 I get

> Your graphics hardware may not be fully supported in Ubuntu 14.04.

And the reason is probably because my hardware is too new and there's no driver. because I bought this PC two days ago.

Should I ignore the message and upgrade ?

---

### Post by Rob Sayer on 2014-09-28
I don't usually worry too much about such messages.  If there's any reliably supported video in linux it's intel.  But best not to assume ...

With this stuff you want to know exactly what you have, and the computer make/model isn't enough.

There are several ways to find out what adapter you have.  See here:

[http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card](http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card)

Then search ubuntu 14.04 + whatever the card is.

If you want to use 14.04, and on a new install that'd generally be my first choice, I prefer a clean reinstall to upgrading.  I highly recommend a separate /home partition.

---

### Post by wadie on 2014-09-28
I'm upgrading right now, if it all works fine then I'll do a clean install again. it's a new pc so I have no data to lose.

Thank you, will keep you posted in case something blows up. :lolflag:

---

### Post by wadie on 2014-09-28
Upgrade done. it's all good,except that it takes some time to respond when opening a program and I keep getting this
> Sorry, the application at-spi2-registryd has stopped working

---

### Post by mörgæs on 2014-09-29
Do you get the same error in a live boot?

---

