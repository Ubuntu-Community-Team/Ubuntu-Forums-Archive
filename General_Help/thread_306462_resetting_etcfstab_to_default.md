---
title: "resetting /etc/fstab to default"
date: 2006-11-25
forum: General Help
---

### Post by Sohum on 2006-11-25
I have done some partitioning.
My /etc/fstab is therefore inaccurate.
The pmounting system is also not working (though this could be unrelated)
Is there anyway of resetting /etc/fstab and pmount and the mounting subsystem in general to the default (i.e., after hardware detection etc.? Like what happens when it first loads up the live cd)?

---

### Post by Voxxi on 2006-11-25
I'm not sure about resetting /etc/fstab, but why don't you just edit it to reflect the new changes? I can walk you through it if you like.

---

### Post by Sohum on 2006-11-25
That might work, but
a) it doesn't fix the pmount problem (ipod etc. not being pmounted. Double-clicking on them in my computer gives "could not run pmount" or words to that effect)
b) i'd have to figure out the uuids of the new partitions. Wouldn't it be simpler to let ubuntu figure them out?

---

### Post by ciastek on 2006-11-26
resetting would be very nice... (and remember - don't use "xxx > /etc/fstab")

---

