---
title: "odd grub problem"
date: 2005-04-15
forum: General Help
---

### Post by feralcelt on 2005-04-15
I dual boot between Ubuntu and Windows the problem i have though is this.

When I reboot the computer a new instance of Ubuntu is created in the loader.

I have about 10 different versions of Ubuntu I can log into and one instance of windows. I look forward to the next time I reboot and have 11 instances of Ubuntu showing up on the list.

Any way to stop this/edit and take out the extra instances of Ubuntu?

Thanks for any help

Brian

---

### Post by nad on 2005-04-15
Please list the available versions. It seems that grub is auto updating. This should happen only upon a kernel addition.

If you are dual booting with XP, please see dozens of threads regarding possible issues.

Dan M

---

### Post by feralcelt on 2005-04-15
[QUOTE=nad]Please list the available versions. It seems that grub is auto updating. This should happen only upon a kernel addition.

If you are dual booting with XP, please see dozens of threads regarding possible issues.

Dan M[/QUOTE]
 I Do dual boot windowsxp I tried doing searches but could not find anything even close to what i'm expieriencing. 

As for the avail versions, some of them it shows with different kernal versions others will have the same one. I'll boot into it and write them down If i can. I'll also do some more searches for issues concerning dual booting with windowsxp

Thanks

---

### Post by alienexplorers on 2007-10-13
Can you list you menu.lst file here:
> cat /boot/grub/menu.lst

---

