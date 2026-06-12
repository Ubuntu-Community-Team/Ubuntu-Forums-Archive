---
title: "Newby problem"
date: 2008-02-28
forum: General Help
---

### Post by TehBlanky on 2008-02-28
hello all , i've got an problem with grub bootloader , let me explain.
i've got an dual boot system , windows xp pro. sp 3 and ubuntu 7.10 .I deleted an ntfs partition (using gparted , restarted , everything was fine) , and added it to an ext3 partition , where ubuntu is located.i gave an restart , and grub started with an error , something like "Error 17" , and i couldn't boot in any os.Is there any solution to repair this situation without installing ubuntu or windows and leave my system intact ? :) 

Thanks

---

### Post by evilc on 2008-02-28
Sounds like you have lost your grub loader, this may help, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by Joeb454 on 2008-02-28
You probably need to reinstall GRUB,  if I remember rightly this can be done from a Live CD :)

---

### Post by tanman on 2008-02-28
If all else fails you could try using a program called GAG. I have used it before and it seems to work really well.
Here is a link to the [GAG Website]("http://gag.sourceforge.net/").
It is a bootloader that loads first and lets you choice what OS or partition to boot into.

---

### Post by TehBlanky on 2008-02-29
DONE! i finally repaired it , i reinstalled grub , thanks to all for your help , really appreciate it :) a

---

