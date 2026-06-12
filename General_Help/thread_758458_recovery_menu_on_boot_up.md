---
title: "recovery menu on boot up"
date: 2008-04-18
forum: General Help
---

### Post by ikt on 2008-04-18
Hi guys and gals,

I have an issue with Ubuntu 8.04, I recently upgraded from 7.10, and ever since then on bootup I get a 'recovery menu' which asks if I want to try and recover x, boot into root shell or boot as normal, if If I choose 'recover x' and then 'boot normally' ubuntu will login normally, however if I don't fix x first, ubuntu will login but have only an 800 x 600 screen resolution.

Can anyone help?

---

### Post by ikt on 2008-04-29
bump

---

### Post by siepo on 2008-05-08
I have this too. Only, if I select `resume' then everything is fine.

---

### Post by ikt on 2008-05-08
> **siepo said:**
> I have this too. Only, if I select `resume' then everything is fine.

I never found out how to fix it, I just reinstalled ubuntu and made it so that /home was on a separate partition so I could always reinstall ubuntu and not worry about wiping my stuff.

---

### Post by siepo on 2008-05-09
I found out where my problem came from: somehow, /boot/grub/menu.lst had gotten messed up during the upgrade. When I fixed it manually, I accidentally left `single' at the end of the kernel line of the main boot stanza. When I removed that, I no longer got the recovery menu.

---

