---
title: "HP DV 4000 partition help"
date: 2014-01-22
forum: General Help
---

### Post by sports fan Matt on 2014-01-22
I have an HP DV 4000 with 512 MB ram and a 100 GB hard drive running Xubuntu.  I need help in trying to get rid of my Ubuntu lucid install so I can save space.  Anyone that can help me through GParted or maybe boot info script?

---

### Post by sports fan Matt on 2014-01-22
screenshot:

---

### Post by mips on 2014-01-23
Whichever OS you were booted into when you took that screenshot is using /dev/sda7 for / and /dev/sda8 for swap, I assume there is no /home partition?

/dev/sda5, dev/sda/9 & /dev/sda6 would belong to the other OS, I'm assuming 5 & 9 would be the root & home partitions, do you have a dedicated home partition in the other OS?

From a terminal the 'df' command will quickly show you which partition is root & which is home for the OS you are booted into.

You also only need a single swap partition between OSes so you could delete both and create a single new one.

---

### Post by sports fan Matt on 2014-01-24
I actually did a bit of tinkering around with the partitions and it seems like I have a lot of unfinished partitions ones I can't move or use etc.  I jut want to for now save SDA 7. Everything else can go to either SDA 1 (Windows) or SDA 7 (Xubuntu 12.04)  How can I clean up what seems to be a lot of mess? Think I'd prefer the extra space to go to my Xubuntu install.

---

