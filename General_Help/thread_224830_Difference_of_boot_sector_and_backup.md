---
title: "Difference of boot sector and backup"
date: 2006-07-28
forum: General Help
---

### Post by meirbenezra on 2006-07-28
when my ubuntu boots while checking for file systems it falls back to the command view that under the hood view you know :) and it says there are differences between boot sector and its backup. I have a hd that is split into three on the first partition there is fat32 and windows installed on the second ubuntu installed the third is used for swap. When I installed ubuntu I used windows' fix mbr to get its bootloader back and installed grub on the boot sector of the second partition.. I was able to load ubuntu from ntloader (windows' bootloader) but now it says sth like this and says not fixing this automatically and it gives what differences there are in numbers like 40:000/BF:00 sth like this (I dont even know how to get the real info copy it and put it here) ubuntu loads fine after that but it annoyed me as a newbie...

---

### Post by meirbenezra on 2006-07-29
so i guess there is not one single thing to do about this??

---

### Post by Herman on 2006-07-29
Hello, meirbenezra,
Windows bootloader is sometimes favoured by a few  people for various reasons, but really, the GRUB bootloader is far superior in almost every way.  It is by far the most popular boot loader for Linux users. I would highly recommend you give it a try. The grub bootloader can do almost anything when we know how. Here's a web-Page explaining a little about Grub, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm").

Re-install Grub with a GRUB shell eg; with Live CD..........................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

               Re-install GRUB....................................(with Alternate CD Rescue mode).......................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")

I hope those links will help you, All the best! From Herman :D

---

### Post by André on 2006-07-29
Hi everybody,

i just wanted to say that this is not a problem with the windows boot loader.

I am using Grub and i get excactly the same error since my last installation. Reinstalling did not work.

@meirbenezra: Did you find any solution so far??

Greetings
Andre

---

### Post by meirbenezra on 2006-07-29
no solutions yet I'm thinking that it is about me installeing grub afterwards. maybe it somehow took the backup of the boot sector and then when I installed grub now the backup and original are different. That's all I can think of no solutions or any other things

---

### Post by meirbenezra on 2006-07-29
I2m using ntloader because all these years I have been using it and I really got used to how it looks like and I can get every os booted with it so why would I need sth new? but thx anyway for your concern.

---

### Post by André on 2006-07-29
Hi,

i tried Mepis these days and i did not have any Error like that.

It has some other problems which distracted me but i am asking myself how this problem occurs.

Is there a way to turn the check off?

Greetings
André

---

### Post by meirbenezra on 2006-07-30
I think solution is not turning the check off cause the system needs to check for stability.. there should be sth else done

---

### Post by odor on 2006-07-31
I have the  same problem... I have two separate hard disks, one with 6.06 LTS and another one with win XP. I have GRU installed, and one day out of the black uBuntu wont load... Reinstalling didn't help, but physically plugging out the disk with XP did... So... it must be the Windows messsing up...

---

### Post by clickwir on 2006-09-16
Boot off Ubuntu or Kubuntu Live CD.
Goto a console screen

sudo fsck -V -r /dev/hda2

choose Y for yes when selected.
If you have Windows on a different partition (maybe /dev/hda1) then use that. Mine and several others were on /dev/hda2.

[http://ubuntuforums.org/showthread.php?t=189472](http://ubuntuforums.org/showthread.php?t=189472)

---

### Post by Lufbery on 2006-09-18
I have the same problem after installing 6.06. It didn't happen with 5.04.

I'll be doing an fsck soon from a live CD. However, how does one fsck a drive that's not mounted?

Regards,

-Drew

---

### Post by PriceChild on 2006-09-18
I used to have this problem... i did resolve it.

I'm very sorry i've since forgotten how to do it, but it involved creating a new bootsector backup.

---

