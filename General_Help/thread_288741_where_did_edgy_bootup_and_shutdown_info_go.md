---
title: "where did edgy bootup and shutdown info go?"
date: 2006-10-30
forum: General Help
---

### Post by NiksaVel on 2006-10-30
Hey all,

I was wondering where did the info messages during boot-up and shutdown screen in edgy go to?  :)

Is there a way to turn them on?  I really appreciated those info options - this is too much xp-like...

---

### Post by slaging on 2006-10-30
Good question. I also enjoy the messages displayed at boot-up/down, and they help identify errors asap. I'm not planning on upgrading my work pc until this issue is solved.

---

### Post by doobit on 2006-10-30
> **NiksaVel said:**
> Hey all,

I was wondering where did the info messages during boot-up and shutdown screen in edgy go to?  :)

Is there a way to turn them on?  I really appreciated those info options - this is too much xp-like...

If you want to see that info, then edit the /boot/grub/menu.lst and remove the word "quiet" from the linux line and the one on it's own line. Then reboot.

---

### Post by bsussman on 2006-10-30
> **NiksaVel said:**
> Hey all,

I was wondering where did the info messages during boot-up and shutdown screen in edgy go to?  :)

Is there a way to turn them on?  I really appreciated those info options - this is too much xp-like...
In case you really enjoy the quiet but still want to view the messages at another time, the command dmesg (for the eariler messages, prior to there being a proper filesystem mounted) and the /var/log directory should have what you need.

---

