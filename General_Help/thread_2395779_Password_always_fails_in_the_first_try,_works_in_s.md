---
title: "Password always fails in the first try, works in second"
date: 2018-07-06
forum: General Help
---

### Post by hipogrito2 on 2018-07-06
Hi,

Ubuntu 18.04

Everytime I have to put the password for sudo or just to log in, it always fails the first time and works in the second. Always. And no, I'm not typing it wrong.

Does anybody have a clue of what's going on?

Thanks,

Regards,
Hipo

---

### Post by mc4man on 2018-07-06
No clue. Just to see something, before typing in password (1st attempt) hit the backspace button, then type password

---

### Post by PaulW2U on 2018-07-07
> **hipogrito2 said:**
> Everytime I have to put the password for sudo or just to log in, it always fails the first time and works in the second.
Does your password start with a shifted character?

If so, [bug #1765261]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1765261") documents a similar bug when logging in but not when prompted for a password after using sudo. The fix is targeted for the 18.04.1 release later this month.

Several similar threads have been started since 18.04's release but I don't think any of them reached a conclusion as to what the cause of the problem is.

---

### Post by hipogrito2 on 2018-07-07
Hi Paul,

That's exactly it. It starts with a shifted letter. I'll wait for a fix then.

Thanks!!!

---

