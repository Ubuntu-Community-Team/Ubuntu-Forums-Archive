---
title: "USB Drive Not Showing Up"
date: 2008-06-19
forum: General Help
---

### Post by Pikestaff on 2008-06-19
Hello,

I have as USB Flash Drive that I have been using for some time now to transfer files between various computers; usually my desktop and my laptop.  As of yesterday it randomly stopped "showing up" on my laptop which runs Kubuntu Dapper.  I would put in the USB stick, the "Do you want to open this in a new window" thing would pop up, I'd say yes, and nothing would happen.  Today, I don't even get that window, putting in the flash drive just does nothing and I can't find a way to access it.

It still works perfectly fine on any other computers of both Linux and Windows operating systems... it's just on my laptop where it randomly stopped working. :-?  Any ideas?

**Edit**: I just now found out I can see the flash drive in media:/ but clicking on it gives me an error.  It also gives me an error when I try to mount it... "An unknown error occurred."

---

### Post by shokoup on 2008-08-28
i have the same problem, it is detected as /dev/sdb1 , when i try to mount manually ,it says that sdb1 not exist

---

### Post by Crafty Kisses on 2008-08-28
Post the results of > lsusb

---

### Post by shokoup on 2008-08-30
> **Codename said:**
> Post the results of > lsusb

thanx for replying,

```
lsusb
Bus 004 Device 004: ID 058f:6335 Alcor Micro Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 041e:405f Creative Technology, Ltd
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

---

