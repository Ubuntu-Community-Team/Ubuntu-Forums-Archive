---
title: "Problem at work: Ubuntu versus IT"
date: 2007-03-01
forum: General Help
---

### Post by floke on 2007-03-01
I have a slight problem (actually more of a fun challenge :) ) looming at work. I have installed Ubuntu as a dual-boot system with XP on my office machine - I have my own office where no IT people come to bother me so that's fine. However, next week an IT engineer is doing the rounds to test our monitors. I won't be in when they arrive, so they will get a bit of a shock to turn on the PC and see Linux loading up :confused: 

So, my question is, how can I rig the machine so that it boots straight into XP and doesn't look like it has Ubuntu on it? My plan is to do this.

(a) Leave Windows running constantly from the last time I am in the office (not very environmentally friendly and will probably crash etc).

OR...

(b) Alter Grub so that it goes straight to XP: So (i) backup grub with 'sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup'; (ii) alter grub so XP is at the top and change the time wait to 0; (iii) hope IT engineer doesn't notice a brief moment of grubness; (iv) when returning to office, mount Ubuntu with live CD and revert to original grub with 'sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst'.

Will this work (or is there an easier way)?

---

### Post by bigken on 2007-03-01
just hold your hands up and let em know you run linux ubuntu and thats why they are never needed :)

---

### Post by floke on 2007-03-01
Now that is tempting.....:)

---

### Post by brazzmonkey on 2007-03-01
alter your /boot/grub/menu.lst. add (without quotes):
"default X"
where X is the default choice (ex : ubuntu is 0, xp may be 1)
"hiddenmenu"
this way grub boot meny won't appear (hit Esc to display the menu)
"timeout n"
where n is the number of seconds before booting default choice.

should enough imho.

---

### Post by Jonne on 2007-03-01
I'd go the edit grub route. Put xp first in the list, and set the wait time to one second. grub will flash on the screen for a second or so, but the dude probably won't notice or care.

---

### Post by floke on 2007-03-01
> **brazzmonkey said:**
> alter your /boot/grub/menu.lst. add (without quotes):
"default X"
where X is the default choice (ex : ubuntu is 0, xp may be 1)
"hiddenmenu"
this way grub boot meny won't appear
"timeout n"
where n is the number of seconds before booting default choice.

should enough imho.

Ah! Sounds good. But where do I put all this stuff?
Say, Ubuntu is the first on the list, do I still have to move XP to the top, or can I just put, say, default 3 (or whatever) as the first line? Also, do I put hiddenmenu as the second line etc.??

---

### Post by brazzmonkey on 2007-03-01
put all this at the beginning of the file.
you don't have to move xp entry to the top, just make sure "default X" points to the correct entry (counting from 0). so if you windows xp entry is the third one, you can get something like this ```
default 2
timeout 5
hiddenmenu
```
i don't think order is relevant.

---

### Post by floke on 2007-03-01
Cheers brazzmonkey!
Much obliged.
I'll practice this tomorrow.

Thanks again.

---

### Post by brazzmonkey on 2007-03-01
you're welcome ! ;)

---

