---
title: "Cannot unencrypt my drive without ´nomodeset´ HELP?"
date: 2016-04-09
forum: General Help
---

### Post by 91122 on 2016-04-09
Dear, Forum

I installed Ubuntu Mate today and installed the drivers + updates.
But now when i boot my pc i dont see the unencrypt partition screen but i see a (-) flasing in white on a black screen endlesly.
I fix this by booting with the ´nomodeset´ then i see the unencrypt partition screen and then can i unencrypt my drive and boot.
Now i got 2 questions 1 Is it bad to boot with nomodeset en does this give problems in the future?
2 If its bad how can i fix that i can boot normaly?

Thanks in advance!!!

91122

---

### Post by deadflowr on 2016-04-09
nomodeset is generally safe.

That said,
To understand more, we would need information about your graphics card and the driver you installed for it.

---

### Post by mc4man on 2016-04-09
> **91122 said:**
> Dear, Forum
Is it bad to boot with nomodeset en does this give problems in the future?


If your drivers (mainly video) support kernel mode setting than the option can produce a degraded experience, though that would also depend on DE. 
Ex., -  Intel gpu/drivers in an ubuntu session would be bad with nomodeset.

If you are using proprietary drivers then they don't support so the option should have no negative performance affect.

---

### Post by Geoffrey_Arndt on 2016-04-09
For those uncommon instances where Ubuntu is not 100% compatible with your HW, doing the full disk encryption at install can present problems that are a PITA to fix.    I'd just reinstall and not select full-disk encryption, and then opt to use a tool like 7zip to encrypt only those directories where it is actually needed.    In my case, that's about 30-35% of my total data, and never includes media.

---

### Post by grahammechanical on 2016-04-10
If nomodeset is getting you to a working desktop then that is good. You are then in a position to change video drivers. How you do that in Ubuntu Mate I have no idea. But I am guessing it is what you need to do. Change video drivers.

Regards

---

