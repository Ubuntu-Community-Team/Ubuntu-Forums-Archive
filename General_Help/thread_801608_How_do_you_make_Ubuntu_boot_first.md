---
title: "How do you make Ubuntu boot first?"
date: 2008-05-20
forum: General Help
---

### Post by jras20 on 2008-05-20
How do I change the boot menu from startup to make Ubuntu boot first?
Its booting up Vista first.
Thanks

---

### Post by Het Irv on 2008-05-20
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

I believe this is what you want.

---

### Post by jras20 on 2008-05-21
> **Het Irv said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

I believe this is what you want.

I wanted to change my windows boot manager to have Ubuntu boot first, it has Vista doing it right now.

---

### Post by Het Irv on 2008-05-21
Oh, You still want to use the Windows, loader... I dunno, I have never used it before.

The instructions I gave you will work I you want to use GRUB.

---

### Post by ibuclaw on 2008-05-21
[EasyBCD]("http://neosmart.net/dl.php?id=1") can apparently do that.

[QUOTE=neosmart.net]
there is no easier way to quickly boot right into Linux, Mac OS X, or BSD straight from the Windows Vista bootloader - on the fly, no expert knowledge needed!
[/QUOTE]

But I wouldn't vouch to that.
Rather, don't knock until you've tried it successfully in a Virtual Environment.

Regards
Iain

---

### Post by Fire_Chief on 2008-05-21
Since you mentioned Vista I'm going to assume you are using the Vista bootloader (bcd, I think it's called). There's a free utility you run from in Windows called EasyBCD. It will allow you to modify the boot menu and set all kinds of options.

Download it [here]("http://neosmart.net/dl.php?id=1")

Cheers!

Edit: Doh, you beat me to it :P

---

