---
title: "can't boot in 386 but can in generic"
date: 2007-01-09
forum: General Help
---

### Post by simonsimon on 2007-01-09
Hi

When I try to boot I get the following message on a black screen and then hang indefinitely:

udevd-event [2751]: run_program: '/sbin/modprobe' abnormal exit

When I choose generic instead of 386 I can boot without a problem.  

I saw a couple of other posts with a similar error and they ended like this: bump....bump...bump...

Any ideas?

On a side note...what's the difference between 386 and generic?

Thanks.

---

### Post by PilotJLR on 2007-01-09
For almost everyone, -generic is the right kernel... the 386 kernel is for older processor (that is obviously a simplification).

Unless you have a reason to use the 386 kernel, just keep using the -generic (and make it the default in grub)

---

### Post by simonsimon on 2007-01-10
Thanks.

Secretly I was hoping that was the answer.

---

