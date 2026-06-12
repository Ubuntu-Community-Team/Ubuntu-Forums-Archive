---
title: "sudo shutdown now via SSH failed"
date: 2007-04-14
forum: General Help
---

### Post by icyisamu on 2007-04-14
I usually boot up my Edgy box and access it via SSH (using putty in Windows).

Was trying to shut down my linux box using the "sudo shutdown now" command, but when I check on my linux box, I am thrown to a terminal and it shows some error message about some process being killed by init or something.

I issued a "sudo shutdown -r now" and my computer rebooted as usual, then I shut it down at the grub menu.

Any one has any idea why this is happening?

---

### Post by kidders on 2007-04-14
Hi there,

> **icyisamu said:**
> Was trying to shut down my linux box using the "sudo shutdown now" command, but when I check on my linux box, I am thrown to a terminal and it shows some error message about some process being killed by init or something.That sounds about right. **shutdown now** should shut down your OS (ie all running processes, not the computer's power).

You may have meant to type **shutdown -h now**. (See **shutdown**'s man page.)

---

### Post by swegner on 2008-03-31
Hi all,

I know this is an old topic, but I just wanted to chime in and say that the -h switch worked for me.  That is, "sudo shutdown -h now".  Couple with wake-on-lan and ssh, this makes remote management very easy and efficient!

---

