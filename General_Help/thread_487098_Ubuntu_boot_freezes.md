---
title: "Ubuntu boot freezes"
date: 2007-06-28
forum: General Help
---

### Post by mrpyo on 2007-06-28
I installed Ubuntu using Wubi and it worked for few times. But now it freezes when starting. 
Funny thing is that there are no errors - it stops after loading kernel (after unpacking those .img files).

When I switch to console there are message "Loading Linux..." (or something like that) and I can wait forever but nothing happens.

I have Dell Latitude D600, hard drive is Toshiba MK4032GAX (40 GB).

---

### Post by mcastel on 2007-06-28
I have more or less the same problem with my laptop Gericom... my system freeze just after the message "activating swap partition..." appears. No problem at all was reported during the installation. What can I do to solve the problem?

---

### Post by ago on 2007-06-28
> **mcastel said:**
> I have more or less the same problem with my laptop Gericom... my system freeze just after the message "activating swap partition..." appears. No problem at all was reported during the installation. What can I do to solve the problem?

Rename c:\wubi\disks\swap.virtual.disk -> c:\wubi\disks\swap.virtual.disk.old 
This will force wubi to skip the swap. See if that helps. In case you can try to regenerate the file with dd.

---

### Post by ago on 2007-06-28
> **mrpyo said:**
> I installed Ubuntu using Wubi and it worked for few times. But now it freezes when starting. 
Funny thing is that there are no errors - it stops after loading kernel (after unpacking those .img files).

When I switch to console there are message "Loading Linux..." (or something like that) and I can wait forever but nothing happens.

I have Dell Latitude D600, hard drive is Toshiba MK4032GAX (40 GB).

I'd need a bit more info. You can try to defragment and running chkdisk.

---

### Post by mrpyo on 2007-06-29
OK it works now. I do nothing and I don't know why but it works.

Anyway thanks for help...

---

### Post by mcastel on 2007-07-17
> **ago said:**
> Rename c:\wubi\disks\swap.virtual.disk -> c:\wubi\disks\swap.virtual.disk.old 
This will force wubi to skip the swap. See if that helps. In case you can try to regenerate the file with dd.

Thanks, now it's working! ;)

Anyway, am I correct that now I am working without a swap area? What can I do to fix the problem (i.e., which is the correcty way to regenerate the swap file)?

Thanks a lot in advance ;)

---

### Post by happydan on 2007-07-20
hi,

just to confuse you a bit more, my problem takes it a step further... i can solve the issue by renaming the swap, but only for one boot. after that, the problem returns. changing the name back to the original then back again solves it once more for a single boot...

this is the second time ive tried to use linux on a pc.

im on a dell inspiron 6400 laptop, btw.

---

### Post by happydan on 2007-07-23
> **happydan said:**
> hi,

just to confuse you a bit more, my problem takes it a step further... i can solve the issue by renaming the swap, but only for one boot. after that, the problem returns. changing the name back to the original then back again solves it once more for a single boot...

this is the second time ive tried to use linux on a pc.

im on a dell inspiron 6400 laptop, btw.


now it wont work at all!

---

