---
title: "remaining Disk capacity in linux"
date: 2005-04-23
forum: General Help
---

### Post by cloudz14 on 2005-04-23
Hi,


I have been using linux for 2-3 years now and I'm pretty newbie interms of knowing linux os. Any one knows how to check remaining disk capacity for ur ext3 ?

I Dun know where to find this information. in uni I just need to type rquota and it gives me disk been used, disk limit, and all that stuff.

How do we find out this information in ubuntu??

Btw UBUNTU ROCKS .. =) I like it.
 O:)

---

### Post by nad on 2005-04-23
df -hl --type=ext3

For all types of filesystems on locally mounted drives, leave off the type argument.

Dan M

---

### Post by cloudz14 on 2005-04-23
thank You so much for the quick reply DAN!

---

### Post by Goober on 2005-04-24
Ohh, thanks for the answer.  Something I had a question about also.

---

