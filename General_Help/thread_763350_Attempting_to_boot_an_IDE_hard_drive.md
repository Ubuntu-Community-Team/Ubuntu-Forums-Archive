---
title: "Attempting to boot an IDE hard drive"
date: 2008-04-22
forum: General Help
---

### Post by xvedejas on 2008-04-22
I might have done something wrong, but I tried to boot an old IDE hard drive on my computer and got this when trying to boot ubuntu;

```
exception Emask 0x0 SAct 0x0 action 0x2 frozen
cmd c8/00:08:00:00:00/00:00:00:00/f0 tag 0 dma 4096 in
status [ DRDY ]
```

I built my computer, and it uses a SATA HDD. I tried to also add the HDD by attaching it to the slave IDE cable; something tells me I did something wrong :(

So what did I do wrong and how can I fix it to access this drive?

---

### Post by logos34 on 2008-04-22
make sure the jumper on the back of the hard disk is set correctly (>'slave' or 'cable select' position).

Check to see if the Bios is detecting it correctly.

---

### Post by xvedejas on 2008-04-23
Alright, it appears I lost the jumper. I'll try to find it tonight.

---

### Post by xvedejas on 2008-04-24
It still doesn't work. Vista will boot (it takes it about twice as long) but I can't get Ubuntu to boot.

---

