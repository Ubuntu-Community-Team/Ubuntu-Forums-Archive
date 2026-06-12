---
title: "Rollback RX vs GRUB"
date: 2014-01-21
forum: General Help
---

### Post by jefgungil on 2014-01-21
Just installed 12.04 as a dual-boot on a new partition. That puts GRUB as the first thing to load. That knocks Windows' [Rollback RX]("http://horizondatasys.com/en/products_and_solutions.aspx?ProductId=1"), which also wants to be first in line, out of commission. I've [searched for solutions]("http://ubuntuforums.org/archive/index.php/t-1005991.html"), but the closest one I can see is by moving GRUB somewhere else. That's apparently over my head so I wonder if anyone here can hold my hand.

---

### Post by jefgungil on 2014-01-21
I just chatted with Rollback and they said fuggedabouit. So never mind, unless you know something they don't.

---

### Post by oldfred on 2014-01-21
A few with encryption have put grub2's boot loader on a flash drive. With flash drive first in boot order.
So without flash drive it boots Windows, and with flash drive plugged in it boots Ubuntu. 

You only need the MBR, but I always do a full install of grub to a flash drive, so I can also use grub to directly boot ISO from flash drive in case I need to make repairs.

---

### Post by jefgungil on 2014-01-21
Thanks. I gave up, deleted the Ubuntu partitions, expanded the c drive, fixed the MBR, un- and re-installed Rollback... like nothing ever happened. But it's nice to know all that can be done and I'll keep your link for next time.

---

