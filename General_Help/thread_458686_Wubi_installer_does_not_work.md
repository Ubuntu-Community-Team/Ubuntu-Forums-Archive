---
title: "Wubi installer does not work"
date: 2007-05-29
forum: General Help
---

### Post by mjs2430 on 2007-05-29
i downloaded wubi, and installed, but at the end it does not ask any questions like shown in the screen shots at wubi's site, it just goes straight to the reboot now or later option. thne when i reboot it is supposed to ask ubuntu or windows but it just goes straight to windows like nothing happened. please help?

---

### Post by tinybit on 2007-05-30
I guess something is wrong with the boot.ini

The boot.ini should be in a primary partition, and in the same folder as NTLDR. But sometimes the drive C: of Windows is not a parimary partition. So we shouldn't use the location C:\BOOT.INI fixedly, I mean, constantly.

---

### Post by ago on 2007-05-30
> **mjs2430 said:**
> i downloaded wubi, and installed, but at the end it does not ask any questions like shown in the screen shots at wubi's site, it just goes straight to the reboot now or later option. thne when i reboot it is supposed to ask ubuntu or windows but it just goes straight to windows like nothing happened. please help?

That is a known bugs, when you have multiple boot.ini the installer might "pick" the wrong one. We'll fix that, in the meantime find the other boot.ini and add "c:\grldr="Ubuntu" and "Timeout=10". You can do that from the control panel. Also copy grldr to the partition containing the boot.ini which is edited. Note that boot.ini might be an hidden file.

---

### Post by timczer on 2007-05-31
I had the same issue.  Everything was where it should be, but no ubuntu choice on reboot.

For me, setting the timeout=30 worked.  I got the OS menu and am in the process of having Ubuntu set up right now.

---

### Post by ago on 2007-05-31
Can you pls try [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

