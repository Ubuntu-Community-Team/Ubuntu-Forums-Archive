---
title: "Cannot Boot"
date: 2015-01-02
forum: General Help
---

### Post by binchunsu on 2015-01-02
I have two OS: Lubuntu and LXLE. So I was editing the Lubuntu partition on LXLE with GParted, "move left and grow". Then, halfway through, it crashed, and when I tried fixing it with "Check", GParted froze. I rebooted and now I can't even get into LXLE: it just shows me this```
Error: Invalid arch-independent ELF magic.
Entering rescue mode...
grub rescue>
```
What can I do now?

---

### Post by justingx2 on 2015-01-02
Boot a live CD/DVD/USB ... then ... 

sudo mount /dev/sda# /mnt
sudo grub-install --boot-directory=/mnt /dev/sda

Where # is your Linux partition. 

Should be fixed.

---

### Post by Bucky Ball on 2015-01-02
I notice this thread is solved. Could you please share how you fixed your issue? Thanks. ;)

---

