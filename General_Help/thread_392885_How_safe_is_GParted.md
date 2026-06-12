---
title: "How safe is GParted?"
date: 2007-03-25
forum: General Help
---

### Post by Doctoxic on 2007-03-25
Hi

I have a dual boot system and want to increase an ext2 partition and take the space from a reiserfs partition AND not lose any data from any of my linux and WinXP partitions.

I have the GParted live CD, but wondered how safe this was - i would assume it should be very safe - but is this the case?

thanks

Doc

---

### Post by hikaricore on 2007-03-25
I've personally never had any trouble with it, and I've seen very few complaints about issues causing dataloss.
However just use your best judgement, dataloss is always possible, but not very likely.

Backup irreplaceable data on cds or dvds if you feel the need to do so

---

### Post by aysiu on 2007-03-25
Backing up your data is the only way to be 100% sure you won't lose anything.

If you don't back up, you can probably be about 99% sure you won't lose anything with GParted resizing.

Just ask yourself--do you want to be 99% sure or 100% sure you won't lose any data?

---

### Post by _duncan_ on 2007-03-25
I used the GParted live CD extensively past 18 months. Resizing existing partitions is one of my major use for it. No problems so far.

But still, I always make sure to back-up existing data just in case something goes wrong.

BTW, it's also considered good practice to defragment NTFS partitions before doing any resizing with GParted.

---

### Post by Doctoxic on 2007-03-25
thanks guys

one more related question - can i change the type of format at the same time with no dataloss - i.e. ext2 to ext4 and reiserfs to ext3?

doc

---

### Post by zvacet on 2007-03-25
I don´t think so,because format will erase data you have.But if I´m wrong,please correct me.

---

