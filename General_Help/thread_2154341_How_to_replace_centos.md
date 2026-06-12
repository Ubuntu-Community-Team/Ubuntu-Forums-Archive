---
title: "How to replace centos?"
date: 2013-06-14
forum: General Help
---

### Post by hodja on 2013-06-14
Hi all,

I have a dual boot machine WinXP/Centos5. I choose the operating system with grub at boot. I want to replace Centos with Ubuntu. What is the best way to do this?

thanks in advance

---

### Post by SeijiSensei on 2013-06-14
Install Ubuntu into the partition currently occupied by CentOS, or repartition the hard drive and create a separate Ubuntu partition, so you can choose between them.

---

### Post by hodja on 2013-06-14
If I do a direct install to centos partition will I loose current grub? This is what I am concerned about. Loosing grub and not being able to boot. How to avoid this?

---

### Post by SeijiSensei on 2013-06-14
Ubuntu will upgrade grub during the installation.

---

### Post by cmcanulty on 2013-06-14
backup your docs and settings first though better safe than sorry!

---

### Post by SeijiSensei on 2013-06-14
If /home resides inside the CentOS partition, then it will be blown away by a new installation.  So, yes, a backup is vital.

If you think you might shop distributions in the future, you would be well advised to create a separate partition for /home.  Then you can change the OS but not lose your files.

---

### Post by hodja on 2013-06-15
Thanks for all the assistance. It worked perfectly.

---

