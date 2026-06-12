---
title: "How do I recover messages shown at the time of booting lubuntu?"
date: 2015-05-30
forum: General Help
---

### Post by arroy_0209 on 2015-05-30
I am using lubuntu in my asus notebook and notice that now a days at the time of booting, a black screen is momentarily shown on which some comments are mentioned. These include some failure issues but since the duration of display is very short, I am unable to read and memorize. There are 4-5 of such notices. How do I recover or see these messages after logging in to my account?

---

### Post by The Cog on 2015-05-30
**dmesg** is the command. ```
dmesg | less
``` will put it into a simple viewer where you can use up/down arrows. Use Q to quit.
The number at the left is seconds since boot.

---

