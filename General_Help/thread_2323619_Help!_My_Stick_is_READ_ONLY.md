---
title: "Help! My Stick is READ ONLY"
date: 2016-05-06
forum: General Help
---

### Post by Rick St. George on 2016-05-06
Wanting to move some files onto my USB Memory Stick, which I used to before, but now an ERROR window pops-up and says "Destination is READ ONLY". 

What could have caused this and how do I fix it???

Thanks!
Rick
:popcorn:

---

### Post by him610 on 2016-05-06
Some USB storage devices have a small sliding switch that can be set to lock/unlock (write/nowrite)

---

### Post by QDR06VV9 on 2016-05-06
And sometimes a simple reboot with stick left in will let you copy to it.

---

### Post by Impavidus on 2016-05-07
The stick might be broken. If a hardware error is detected, the stick becomes read-only.

---

### Post by leunam12 on 2016-05-07
Sometimes a USB stick will say that it's read-only and blah, blah, what not; sometimes this works to fix it. ```
sudo dosfsck -a /dev/sd(x#)
``` Do not type the parenthesis. the x represents the letter assigned to your USB stick and the # is the partition number. To find out what letter and number use lsblk on the terminal.  The actual command would be something like this ```
sudo dosfsck -a /dev/sdg1
``` This is just an example, use the letter and number given by lsblk. then, pull the stick and re-insert it.

---

### Post by Rick St. George on 2016-05-07
Strange! After popping it in to try the above, it worked without trying the above.
Will post as solved.

Thanks!

---

