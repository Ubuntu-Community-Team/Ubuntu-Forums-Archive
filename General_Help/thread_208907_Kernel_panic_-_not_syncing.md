---
title: "Kernel panic - not syncing"
date: 2006-07-04
forum: General Help
---

### Post by SPlutard on 2006-07-04
I put my laptop into "Hibernate" mode before bed last night, and now when I try to turn it on, it spits out this text on a black screen:


Code:
```
Uncompressing Linux... Ok, booting the kernel.
Loading, please wait...
.: 17: Can't open /scripts/functions
[4294669.284000] Kernel panic - not syncing: Attempted to kill init!
[4294669.284000] 
```
The cursor just sits there. All I can think that I did to it was install a couple of (seemingly) routine updates yesterday. Heh - how come this sort of thing happens right before you were about to back it all up? Also, I'm not sure if it'll make a difference, but I have a removable internet card that I use, but I've never had any problems with it. Though would it matter if I put the comp in Hibernate, then removed the card before the comp woke up?

I searched the forums, and though I didn't find an answer to my problem, I did read that it might be possible to switch to another version of the kernel? If this sounds stupid, it's because I'm just a newb; I've only been using Ubuntu for about 2 months... 
Thanks.
SP

---

### Post by FenrisAbraxas on 2006-07-04
When you are booting at the "GRUB loading" press esc, then select another option there or enter the default kernel in recovery mode.

Hope it helps :)

---

### Post by SPlutard on 2006-07-04
Hmmmm - that appears to have worked. Thanks!

Will this happen every time I try to start up? If so, then is there a more permanent solution now that I'm "in"?

---

### Post by stewarma101 on 2006-07-09
try removing all but one stick of ram

---

