---
title: "problem with deleting old ubuntu linux 8.04"
date: 2008-05-06
forum: General Help
---

### Post by Turge on 2008-05-06
hello !
i installed the ubuntu again on my free space and now i don't know how can i delete the old ubuntu.
so i go to the folder and try to delete that and it's don't let me to do that, so someone know how can i delete the old ubuntu?

both of them are 8.04.
and i know what is the old and what is the new, so can somebody tell me with something to put in the terminal maybe and that it's will let me to delte that?

thx anyway.

---

### Post by abbot on 2008-05-06
you'd have to delete the partition that the other one is installed on.  gparted would work.  look for "gnome partition editor" in the add/remove software.  then you can probably expand your good installation's partition into the deleted space, but i've not really messed with that before.  i know that ext3 is funny about partition resizing because of how it writes files, but i wouldn't think that increasing the size would pose much of a problem.

a 2nd opinion would be nice here.

---

### Post by abbot on 2008-05-06
whoops.  double post.

---

### Post by Turge on 2008-05-28
> **abbot said:**
> you'd have to delete the partition that the other one is installed on.  gparted would work.  look for "gnome partition editor" in the add/remove software.  then you can probably expand your good installation's partition into the deleted space, but i've not really messed with that before.  i know that ext3 is funny about partition resizing because of how it writes files, but i wouldn't think that increasing the size would pose much of a problem.

a 2nd opinion would be nice here.
I installed the software and i don't find where is it.
can someone can help me where do i find it?

---

