---
title: "Reset Root Password"
date: 2007-12-23
forum: General Help
---

### Post by PewPew Lazer on 2007-12-23
Hello. So my grandpa decided to install Ubuntu on his computer.
Alls well, but he forgot his password therefore cannot log in.
Is there something he can do to change the root password without logging in?

And no, I'm not my 'grandpa'. :P

-Pew

---

### Post by p_quarles on 2007-12-23
By default, Ubuntu doesn't configure an actual root password. I'm guessing that what you want to do is resent *his *password, which is easy enough.

During the GRUB bootup process, you should select "Recovery Mode". If you don't see this option, it's because the GRUB menu is hidden -- press the escape key to show it. This happens right after the BIOS is finished loading. 

Once you're in recovery mode, you can reset the password like so:
```
passwd *grandpa's-username*
```
It will prompt you type the new password twice, and you're done. He can now boot into normal mode and log in to his account.

---

### Post by PewPew Lazer on 2007-12-23
Ah thanks a lot :)
I'll let him know.

-Pew

---

