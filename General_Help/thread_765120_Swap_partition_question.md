---
title: "Swap partition question"
date: 2008-04-24
forum: General Help
---

### Post by roccivic on 2008-04-24
I would like to install 2 instances of Ubuntu (8.04) on my PC.
Do I need 2 separate SWAP partitions or can 1 be shared between both operating systems?

Thanks, Rouslan

---

### Post by overdrank on 2008-04-24
> **roccivic said:**
> I would like to install 2 instances of Ubuntu (8.04) on my PC.
Do I need 2 separate SWAP partitions or can 1 be shared between both operating systems?

Thanks, Rouslan

HI and Ubuntu should share the swap. If I may ask why 2 ?

---

### Post by unutbu on 2008-04-24
One swap will do.
Each partition will have a file called /etc/fstab. That file defines which partition (e.g. /dev/sda*) is to be used as swap space.

---

### Post by munkyeetr on 2008-04-24
share +1...er, +2

---

### Post by Monicker on 2008-04-24
> **roccivic said:**
> I would like to install 2 instances of Ubuntu (8.04) on my PC.
Do I need 2 separate SWAP partitions or can 1 be shared between both operating systems?

Thanks, Rouslan


They can share the same swap partition.

---

### Post by roccivic on 2008-04-24
Thank you.

I have to share the computer with my girlfriend. But don't want to have just 2 separate accounts within 1 operating system, just in case she will mess things up. Oh, and she'd like to have root privilegies, too.

BTW, what would be a good size for the SWAP partition? (Specs: 2.4GHz CPU, 512MB RAM, 160GB HDD.)

Rouslan

---

### Post by overdrank on 2008-04-24
> **roccivic said:**
> Thank you.

I have to share the computer with my girlfriend. But don't want to have just 2 separate accounts within 1 operating system, just in case she will mess things up. Oh, and she'd like to have root privilegies, too.

BTW, what would be a good size for the SWAP partition. (Specs: 2.4GHz CPU, 512MB RAM, 160GB HDD.)

Rouslan

HI and the rule of thumb is twice the memory. :)

---

### Post by roccivic on 2008-04-24
Thank you all guys very much.

Rouslan.

---

### Post by nsche on 2008-04-24
But that rule really doesn't make any sense.  You need enough swap to accomodate whatever memory overdraft you will want to operate with.  For a given level of usage the more memory you have the less swap you will need.  The presumption is that if you have more memory you will try to do more with it so you will have a greater need for swap.

---

