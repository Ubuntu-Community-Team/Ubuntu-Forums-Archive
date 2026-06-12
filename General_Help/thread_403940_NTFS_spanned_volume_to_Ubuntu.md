---
title: "NTFS spanned volume to Ubuntu"
date: 2007-04-07
forum: General Help
---

### Post by DannyW on 2007-04-07
Hi, I'm new to linux. Finally got Ubuntu working ok(ish).

Before I decide to scrap windows completely though I need to get everything perfect in Ubuntu.

On windows I have a logical volume spanned across three drives making the total size around 600GB.

Is it possible to convert this to a form Linux can use?

Thanks in advance,
Danny.

---

### Post by spankymasterc on 2007-04-07
ok how many Hd do you have? and yes u can convert the hardrive to ext3 so linux could use it id recommend to have a partition of about 30-40 gigs for linux and then make a partition that is ext3 expansion to it so you can use it for linux this is my setup 

Windows vista (partitoin)
ubuntu (ext3) 30 gigs
ubuntu (ext3 extended partiton) another 30 gigs from another hard drive
and the rest it a 200 gig partition

i have two 250 gigs :D ::cheers:::

---

### Post by DannyW on 2007-04-07
I have 4 drives:

80GB
200GB
300GB
400GB

(Don't know the exact sizes but this is roughly it, +/- 50GB)

I would like it to be set up as follows:
80GB: 40GB Ubuntu; 40GB Windows
200GB: 30GB Other; 170GB [spanned] 
300GB: [spanned]
400GB: [spanned]

This is similar to how I have it set up now. Only the spanned volume is ntfs and not viewable to linux. Could I convert this to ext3 (is this the best option?) without losing my data?

Thanks for the speedy response,
Danny

---

### Post by DannyW on 2007-04-08
bump

---

### Post by der_joachim on 2007-04-08
You cannot convert an NTFS partition to ext3 without losing the data. I'd make a backup of everything and delete the partitions altogether.

---

