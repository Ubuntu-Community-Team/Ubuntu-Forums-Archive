---
title: "[SOLVED] boot windows vista x64 from grub"
date: 2008-05-22
forum: General Help
---

### Post by sokopok on 2008-05-22
Hi,

I recently installed m$ windows vista x64 next to my usual ubuntu (8.04) system. Now I'm having some trouble getting it to boot via grub. No matter what I try, I always get: error 13 unrecognised executable format.

However, I can boot using a supergrub bootdisk (using following procedure: Windows/Advanced/Boot Partition/...).

The relevant section in my /boot/grub/menu.lst is as follows:
  title Windoze Vista
  rootnoverify (hd0,3)
  makeactive
  chainloader +1

Anybody got any ideas on how to get this to work?

---

### Post by meierfra. on 2008-05-22
Open a terminal in ubuntu and post the output of

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

(both "l" are lowercase "L")

---

### Post by sokopok on 2008-05-23
Thanks meierfra for your reply, but my apologies for the trouble. It was a little oversight from my part.
I had such a hard time getting a clean install of Vista x64 to boot (several reinstalls, lots of forums, ms support pages, and almost 2 days) that I started trying all kinds of things to get it to work. In the end I move my Vista partition (which was /dev/sda4) to /dev/sda3, so I still had sda4 in my head (and in menu.lst). This didnt work eather, so in the end I had to disable SATA and use plain ATA controller. It's running now (more or less). Thanks you Microsoft, thank you Dell for a very unproductive 2 days.
So consider this thread closed.

---

