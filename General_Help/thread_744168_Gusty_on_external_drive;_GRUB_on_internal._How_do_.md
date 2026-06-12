---
title: "Gusty on external drive; GRUB on internal. How do i move it to external?"
date: 2008-04-03
forum: General Help
---

### Post by nappymonster on 2008-04-03
Not sure which forum this belongs to, so posting in general.

hi all,
I had an old laptop drive that i put inside a case, and now plug it in via USB. I installed gusty a few weeks ago, but it decided it wanted to put GRUB on the internal drive. That's fine, except:
-If (Or when in my experience) grub messes up, i want to be able to still acess vista.
-I want to have a 'portable' ubuntu, not just on this PC.

So how do i put GRUB on the external drive? Just copy the C:\Boot folder across and change all the HDA 1's to HDA 0?

Thanks,
Nappymonster

---

### Post by strabes on 2008-04-03
You should just install grub onto the external HDD. The wiki page linked to in my sig tells you how to do this in pretty good detail. You would just install it to /dev/sdb1 or whatever. If you need help on grub partition naming conventions, check this page: [http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html](http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html)

---

### Post by pcmann2004 on 2008-04-03
hey there,
what about haveing windows on hdd0 and ubuntu on hdd1 and haveing grub manage both

---

### Post by nappymonster on 2008-04-03
Thanks Strabes, but:
Will installing over the MBR ruin my vista internal hard drive?
Do any of those commands need to be edited for use with external hard drive?

---

### Post by nappymonster on 2008-04-04
Bump

---

