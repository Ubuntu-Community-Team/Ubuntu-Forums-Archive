---
title: "Dual boot question"
date: 2013-08-10
forum: General Help
---

### Post by Erik_Madison on 2013-08-10
Hey-
 I'm new to this whole "Ubuntu" thing and have recently set up my Sony Vaio laptop as a dual boot with 13.04. Whenever I start up my computer, it first takes me to the Ubuntu boot directory. From there, if I choose Windows 7, it takes me to the Windows boot manager where the only option is to choose Windows 7. I was wondering how I could set it up so that it only takes me to one of the two OS's boot managers, instead of running me through both of them every time I start my computer. 

Thanks,
         Erik

---

### Post by meilin on 2013-08-11
You can skip or hide Windows 7 boot loader while booting. Search it on Google or see the link below:

[http://www.intowindows.com/how-to-skip-or-hide-windows-boot-manager-in-vista-and-windows-7/](http://www.intowindows.com/how-to-skip-or-hide-windows-boot-manager-in-vista-and-windows-7/)

Another way is to add Ubuntu to Windows 7 boot loader and then hide Ubuntu bootloader (grub), but it's complex. So I recommend the first way.

---

### Post by grahammechanical on 2013-08-11
There is a saying. Be careful for what you wish for. You may get it.

At the moment you have a bootloader that boots both Ubuntu and Windows 7. It is not elegant but it works. You may end up with Windows 7 loading and no option to load Ubuntu. Or, only an option to load Ubuntu and no option to load Windows.

Some posting on this forum have had those problems - Ubuntu without Windows or Windows without Ubuntu. You have both.

Regards.

---

### Post by oldfred on 2013-08-11
I thought Windows only showed its boot menu if you had multiple Windows entries. Did you have multiple installs before?
Or it may be a setting in the BCD. I might review your BCD with bcdEdit.

 [http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

If you get grub menu first it is not a wubi install inside Windows. Is it a new system with UEFI?

---

