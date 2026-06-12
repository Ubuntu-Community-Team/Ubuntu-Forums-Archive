---
title: "no boot loader screen"
date: 2013-09-02
forum: General Help
---

### Post by christina5 on 2013-09-02
cannot get to Ubuntu

have XP and Ubuntu 12 in a dual boot system. have been in Windows environment too long.
screen does not give me the chance to call Ubuntu - just boots to Windows.

---

### Post by rai_shu2 on 2013-09-02
You might need to [reinstall Grub2]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2").

---

### Post by Bashing-om on 2013-09-02
christina5; Hi ! ... Welcome to the forum .

Sounds like you have lost the bootloader to load ubuntu. Fixable.
As you are new to ubuntu, let us do this in small steps.
1st we need to know what your hard drive arrangements are to know for sure where to install grub (GRand Uninfied Bootlader);
a) Bootup the liveDVD to the ubuntu desk top in "try ubuntu mode" //the key combo ctl+alt+t yields a terminal; post back to us - between code (#) tags - top of post- the output of terminal code:
```

sudo fdisk -lu

```
b) Once this is known, we can provide you the commands to mount that partition containing ubuntu, and the command to install "grub" in the appropriate place.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

