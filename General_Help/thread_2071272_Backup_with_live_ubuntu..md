---
title: "Backup with live ubuntu."
date: 2012-10-15
forum: General Help
---

### Post by marjoh05 on 2012-10-15
Hi!

Im working at a school where there are a good share of Macbook's.

At all time we have about 3-4 of maybe 200 inn because of a bad system or harddrive (The students treat them like sh*t).

Ofcourse they dont have any backup, so i got to try to save as much as i can.


With normal computers i use live ubuntu, at that works at all time.

But i with mac i have user right issues, i have tried nautilus etc.

They wont let me make folders or drop any information into the harddrive! I have been using FAT32 system, that should work on every system right? The disk works rigth on any other computer, just not the live ubuntu on mac.

Any clue?

Regards!

---

### Post by Bucky Ball on 2012-10-15
But the Live Desktop sees the external hard drive ok? If so, you can open Nautilus by opening a terminal and:

```
sudo nautilus
```Now you should have temporary permissions. ONLY move the files in Nautilus as you are root until you close Nautilus so you can cause some damage intentionally or otherwise.

---

### Post by marjoh05 on 2012-10-15
It can see the external HDD.

I have tried Sudo Nautilus, but there is no difference.

---

### Post by shreepads on 2012-10-15
Can you pull the drives out of the Macbooks? If yes, put them into an external USB enclosure and plug into your standard Linux machine's USB interface...

Could also plug directly into a eSATA connector once pulled out...

---

