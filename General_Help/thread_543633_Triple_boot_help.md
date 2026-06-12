---
title: "Triple boot help"
date: 2007-09-05
forum: General Help
---

### Post by JSpencer87 on 2007-09-05
For what I do I need both Windows XP and linux my choice being feisty.  Yesterday I decided to go out and get vista for the hell of it and try it out.  But now the vista boot loader wont let me boot into linux.  I am able to boot into XP and vista fine.  I know that I can edit and restore grub from a live cd but I am hesitant for fear of losing one of the other OS's.  I don't care about getting just one boot loader or having a chain, I just want to be able to boot into all three OS's.  Thanks in advance.

Justin

---

### Post by Allanon.gc on 2007-09-05
Try this boot loader program for vista first of all if you haven't gotten XP and Vista together [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1). It's called Easy BCD and I'd install that, run it on vista and then reinstall grub. Since grub only recognizes windows as an entirely separate boot loader, it won't ruin either ones. However I've only done this once so I'm not 100% positive.

---

### Post by rsambuca on 2007-09-05
I have never used the EasyBCD so I can't give advice on that, but I have always just used grub.  You can easily re-install grub using the live CD.  It will automatically detect the Vista bootloader and you can go from grub loader to vista loader to either vista or xp.

---

### Post by JSpencer87 on 2007-09-05
Ok thanks, I wasn't sure if Grub would recognize the Vista boot loader like that, I will reinstall it.  Thanks again.

Justin

---

