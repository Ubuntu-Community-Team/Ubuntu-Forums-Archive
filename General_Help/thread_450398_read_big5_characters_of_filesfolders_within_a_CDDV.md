---
title: "read big5 characters of files/folders within a CD/DVD"
date: 2007-05-21
forum: General Help
---

### Post by chunchengch on 2007-05-21
If you need to read **big5** characters, such as Chinese characters, of files/folders within a CD/DVD, following procedures may be useful, at least it works for me.

**1. Open file fstab:**

    sudo gedit /etc/fstab

**2. Replace black bold text with red text:**

     /dev/scd0 /media/cdrom0 udf,iso9660 user,**noauto 0 0**
     /dev/scd0 /media/cdrom0 udf,iso9660 user,[COLOR="Red"]**noauto,iocharset=utf8 0 0**[/COLOR]

**3. Reboot and check CD/DVD.**

---

