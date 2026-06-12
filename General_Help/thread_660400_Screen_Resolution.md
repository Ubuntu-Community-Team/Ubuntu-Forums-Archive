---
title: "Screen Resolution"
date: 2008-01-06
forum: General Help
---

### Post by hds272 on 2008-01-06
My screen resolution is always set to the highest and it will not lower although it has in the past, any suggestions?

Thanks,
HDS

---

### Post by lmlypfan on 2008-01-06
I'm assuming you can't adjust in under the systems tab?

---

### Post by hds272 on 2008-01-06
yes

---

### Post by lmlypfan on 2008-01-06
Have you tried to reconfigure the xserver?

sudo dpkg-reconfigure xserver-xorg

---

### Post by hds272 on 2008-01-06
> **lmlypfan said:**
> Have you tried to reconfigure the xserver?

sudo dpkg-reconfigure xserver-xorg

How do you do that?

By the way im using vmware if that makes a difference.

---

### Post by lmlypfan on 2008-01-06
restart your computer
boot into recovery mode.

enter the command I posted above.

Follow the configuration prompts.

You'll select your driver in one of the first steps.  After you restart, you should be able to change res.

Also, what graphics card are you using?  Have you tried the restricted drivers?

---

### Post by lmlypfan on 2008-01-06
BTW, I'm not sure how vmware will affect this

---

