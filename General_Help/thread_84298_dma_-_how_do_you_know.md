---
title: "dma - how do you know?"
date: 2005-10-30
forum: General Help
---

### Post by bionnaki on 2005-10-30
how exactly do you know if you need dma support?

---

### Post by aysiu on 2005-10-30
If you don't know if you need it, you probably don't.

---

### Post by drummer on 2005-10-30
I don't know about dma on hard drives, but you'd notice it if it wasn't enabled on a dvd drive.. movies would be a bit choppy because the drive often can't transfer the data fast enough without dma. To check for it, open a terminal and do "sudo hdparm /dev/hdb" (without the quotes, and replace hdb with whatever the drive is)

---

### Post by dtfinch on 2005-10-30
You don't really need it, at least not in a life or death sense. You should always want it though, especially on DVD's. There's absolutely no reason to leave it disabled if your hardware supports it properly.

---

