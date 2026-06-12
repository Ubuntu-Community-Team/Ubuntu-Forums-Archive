---
title: "Dual booting windows xp and ubuntu"
date: 2008-05-14
forum: General Help
---

### Post by blinded on 2008-05-14
Hello,

I installed Ubuntu yesterday in a free partition I had. However, when I turn the computer it doesn't give me the option to choose XP or Ubuntu, it just sends me directly to Ubuntu. How can I access Ubuntu, and how can I have it give me the option of either accessing XP or Ubuntu ?

---

### Post by joshsmith on 2008-05-14
are you sure there isnt a point during the boot process where it says press esc for options or something like that, or maybe the timeouts are too quick, and you are missing it?

did you install it from windows (wubi) or from the live cd

do you still have access to your windows drive, from the file browser in ubuntu. (it should be in the left panel of the file browser)

if you run in the terminal, and post the output of 
cat /etc/fstab
this will give detailed info about your hard-drives, which you or someone here will be able to look through to help

---

### Post by kirios on 2008-05-14
Post the contents of your */boot/grub/menu.lst* file.

> **blinded said:**
> Hello,

I installed Ubuntu yesterday in a free partition I had. However, when I turn the computer it doesn't give me the option to choose XP or Ubuntu, it just sends me directly to Ubuntu. How can I access Ubuntu, and how can I have it give me the option of either accessing XP or Ubuntu ?

---

