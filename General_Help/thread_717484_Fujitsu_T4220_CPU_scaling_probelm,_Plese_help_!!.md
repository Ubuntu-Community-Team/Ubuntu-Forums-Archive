---
title: "Fujitsu T4220 CPU scaling probelm, Plese help !!"
date: 2008-03-07
forum: General Help
---

### Post by haplo_09 on 2008-03-07
Hi, everybidy who uses t4220. 

I wold like to know if anybody managed to enable cpu scaling on their fT4420 laptop, and if yes could you write a shourt outline how you did that. specifically what updated version of DSDT you used and how ou updated it. Because the guide that was written earlier is
[https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)


 quite confusing and some of the things doesnt work, such as "permission denie" message, and also, should onl one file from the whole package be used (DSTD.) was confusing and difficult to unederstand. 

thanks you

---

### Post by haplo_09 on 2008-03-07
Also, the fix seems to be not present in hardy alpha 6. What do you guys think?

---

### Post by haplo_09 on 2008-03-07
BTW also, does anyone know where to enable acpi_osi= as mentioned in fujitsu t4220 manual?

---

### Post by ranpha on 2008-04-26
in /boot/grub/menu.lst 

you need to make a manual entry and add the acpi-osi command to it

---

