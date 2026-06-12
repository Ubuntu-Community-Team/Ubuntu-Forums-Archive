---
title: "first log on"
date: 2005-10-17
forum: General Help
---

### Post by npodges on 2005-10-17
I just installed 5.10. after starting the install, it reboots and then finishes the last part. after the last part, it reboots once more, then it should actually boot up. instead it gets to the boot up screen where it shows all of the initialization processes and says okay. after that is all done, it goes to a blank black screen with the blinking cursor in the top left corner. after about 5 seconds, that cursor stops blinking and becomes frozen. i figured it was 100% frozen, until i tried ctrl alt f1-f6, and the all work. it seems to be working fine, except it never opens up. it didnt give me an error when starting X, but it just hangs up at that point. any ideas?
-thanks

---

### Post by bluck on 2005-10-17
[QUOTE=npodges]I just installed 5.10. after starting the install, it reboots and then finishes the last part. after the last part, it reboots once more, then it should actually boot up. instead it gets to the boot up screen where it shows all of the initialization processes and says okay. after that is all done, it goes to a blank black screen with the blinking cursor in the top left corner. after about 5 seconds, that cursor stops blinking and becomes frozen. i figured it was 100% frozen, until i tried ctrl alt f1-f6, and the all work. it seems to be working fine, except it never opens up. it didnt give me an error when starting X, but it just hangs up at that point. any ideas?
-thanks[/QUOTE]


what does the output of `dmesg` say?

also, i had a similar prob with a dell inspiron laptop.  fixed it by changing the driver in my xorg.conf to 'vesa'

kind of a kludge..  but it works.

---

### Post by npodges on 2005-10-17
well, it says about three pages of things. is there anything in particular i should be looking for?

---

