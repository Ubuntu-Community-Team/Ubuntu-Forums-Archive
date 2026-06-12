---
title: "Help creating a new swap partition"
date: 2006-12-15
forum: General Help
---

### Post by raul_ on 2006-12-15
So i've installed Ubuntu and I didn't know i would need a swap partition :mrgreen: Now I want to create a new one.
So I open GParted, select my windows drive (the one i want to resize) and there is no resize/move option, only "Delete" or "Format To".
Why does this happen?

---

### Post by lha on 2006-12-15
Creating a partition is not your only option. You can alternatively create a swap file: [http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html") Look at 'To add a swap file:'.

---

### Post by meng on 2006-12-15
Depends on the version of GParted. The latest version has more broad support for move/resize. Also, don't mess around with GParted while you have your installed Ubuntu running, try downloading the latest version of the GParted LiveCD and booting from that to repartition.

---

### Post by raul_ on 2006-12-15
> **lha said:**
> Creating a partition is not your only option. You can alternatively create a swap file: [http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html") Look at 'To add a swap file:'.

But then i'll eat up space from my Ubuntu partition...and i didn't want that. Still, it's a good idea, it will just take me a little longer :)

---

