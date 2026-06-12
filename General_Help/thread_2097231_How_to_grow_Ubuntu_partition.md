---
title: "How to grow Ubuntu partition"
date: 2012-12-22
forum: General Help
---

### Post by jweaver682 on 2012-12-22
Hello, I currently have a 195 gb windows partition and a 29 gb Ubuntu partition. I want to grow the Ubuntu partition, but I am having a hard time. I tried shrinking the Windows partition down to 175 gbs, and leaving 15 to add to the Ubuntu partition. However, after I make the free space a partition, I can't grow the Ubuntu partition that is right in front of it. Does anyone know what to do to fix this? I am really new to managing partitions, so if anyone has any ideas it would be appreciated.

---

### Post by Ms. Daisy on 2012-12-22
You have to boot from a live CD and run gparted from that. If you see a lock icon on any of the partitions you need to right-click and choose "unmount".  

When I tried to grow a partition to the left, I found that I needed to first move the partition to the beginning of the free space, wait for that to complete, then expand the partition to the right.

---

