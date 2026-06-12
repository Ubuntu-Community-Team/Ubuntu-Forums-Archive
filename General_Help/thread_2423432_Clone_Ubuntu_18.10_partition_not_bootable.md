---
title: "Clone Ubuntu 18.10 partition not bootable"
date: 2019-07-23
forum: General Help
---

### Post by cablefreeantonio on 2019-07-23
Hello,

I have cloned one partition with Ubuntu 18.10 to another partition on the same disk, as expected the other partition is not showing on boot list, so I generated a new UUID to the second partition using Gparted, so I booted to the original partition and can now see the other one and mount it. So, now I would like to know how to make both partitions show on the boot list so I can choose either of them to boot to. Tried many tutorials but none of them worked.

---

### Post by uRock on 2019-07-23
Hello and welcome to the forums,

Open a terminal and run this command. It should work after that.

```
sudo update-grub
```

---

### Post by cablefreeantonio on 2019-07-23
Great, it worked! Thanks.

The amount of tutorials out there that show a lot of commands that don't work is overwhelming and all I needed was a single one.

---

### Post by uRock on 2019-07-23
> **cablefreeantonio said:**
> Great, it worked! Thanks.

The amount of tutorials out there that show a lot of commands that don't work is overwhelming and all I needed was a single one.

Awesome, I'm glad that worked out. There are definitely tutorials out there that can lead you in the wrong direction and some of them aren't written very well.

Be sure to mark this solved by clicking on Tread Tools in the upper right and selecting Solved.

---

