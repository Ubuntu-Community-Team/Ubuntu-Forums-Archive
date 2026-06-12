---
title: "Invalid disk usage in Ubuntu 18.04 LTS"
date: 2022-11-03
forum: General Help
---

### Post by jigarpatelp on 2022-11-03
Hello,

I'm using Ubuntu 18.04 where i've enough disk space showing in gparted for /dev/sda6 which is rootfs but while looking into system monitor app it show different space available and warn for low disk usage.
Here i've attached screenshot for the system.
How to resolve this.
Any suggestions?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291222&stc=1[/IMG]

Thanks

---

### Post by Impavidus on 2022-11-03
Some of the filesystem (by default 5%) gets reserved for emergency use, making it available to the root user only. You can tune this (look into tune2fs and change the reserved block percentage), but you'll gain at most 5% as your drive really is nearly full.

Running your filesystem over 90% full increases fragmentation, which slows access to your filesystem down (on spinning drives at least).

---

