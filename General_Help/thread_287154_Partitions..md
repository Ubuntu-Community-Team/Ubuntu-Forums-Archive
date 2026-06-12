---
title: "Partitions."
date: 2006-10-28
forum: General Help
---

### Post by bugz0r on 2006-10-28
If I create a new partition for Edgy, can I move files from my Dapper partition onto my Edgy partition? Furthermore, could I delete one of the partitions in any way?

---

### Post by DaveBorealis on 2006-10-28
> **bugz0r said:**
> If I create a new partition for Edgy, can I move files from my Dapper partition onto my Edgy partition? Furthermore, could I delete one of the partitions in any way?

Hello,

You can move any file from the Dapper to the Edgy partition, but I would not move any system files (or applications/application files) because you'd be opening the door to incapatibilty hell.  If you install Edgy and launch it, you could then mount the old Dapper partition and save to and from it without problem.

Once you move the wanted files over to Edgy, you could delete all that's on the old Dapper partition and use it as you would use any other mounted directory.

Best regards,
Dave

---

### Post by bugz0r on 2006-10-28
I just realized the stupidity of my post. Of course I can move files from one patition to the to other! But can I remove the Dapper partition, as in not have it there at all, as in just have one whole hardrive?

---

### Post by DaveBorealis on 2006-10-28
> **bugz0r said:**
> can I remove the Dapper partition, as in not have it there at all, as in just have one whole hardrive?

No problem at all.  Make certain you save off drive any files that you want, then during the install delete the existing partitions and do the repartition/reformat processes.  You will, however, still have to have a minimum of two partitions, one for root ('/') and one for swap.  (Technically you don't really need a swap, but that's not recomended for the likes of us destop user types!)

Dave

---

