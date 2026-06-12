---
title: "corrupted winload cannot boot ubuntu12.04  with dualboot window7"
date: 2013-04-03
forum: General Help
---

### Post by aritari on 2013-04-03
window7 fail to repair corrupted winload .sombody please help me on this issue

---

### Post by Kirboosy on 2013-04-03
Welcome to the forums!

So right now the system will not boot anything that is on it?

---

### Post by Mark Phelps on 2013-04-03
I don't believe you can "repair" a corrupted winload.exe file -- if that is the problem you have.

You could try Boot-Repair (see link), but it might not work: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

IF you have a Win7 Repair CD, or a Win7 installation DVD, you should be able to boot from that -- but if you can do that, you should go to the Windows 7 forums (sevenforums.com) and see what tutorials they have on doing repairs from a command line.

---

### Post by Kirboosy on 2013-04-04
[Windows Tips]("http://answers.microsoft.com/en-us/windows/forum/windows_7-system/unable-to-fix-winloadexe-corrupt-error-using/9a2b701c-b3e6-4e86-bcb1-36e466edbc96?msgId=9d1c8935-bfd6-43e2-b40d-21bbfe84d855")

+1 on the Boot-Repair tool. Super handy tool to have in your bag of tricks.

Also if all else fails you can boot into a liveCD and backup all the data off the computer. Wipe and reload Windows and Ubuntu. Make sure to install Windows first and then Ubuntu. Otherwise Windows will wipe out grub and you will have to go back and install GRUB again.

---

