---
title: "Do I really need Grub ????? Windoz free at last"
date: 2007-03-01
forum: General Help
---

### Post by kindafunnylookin on 2007-03-01
I have 2 HDD's with Edgy on the master and Windows on the slave. I just made the leap and formated the slave as ext3 and I'm planning on using it for Partimage backups and for my music & Photo storage.

My question is - do I still need Grub with only one OS, and if not - how do I get rid of Grub?
PK

---

### Post by jocko on 2007-03-01
Yes, you will always need a boot loader.

---

### Post by russo.mic on 2007-03-01
I think what above means is,  to be more in depth, you always need a boot loader.  But you CAN however configure it so that it doesn't ask you what OS you want to boot into, as you'll only have one anyway.  The easiest way is to edit you config files and set the boot delay as 0, and it will just boot into you default OS.

---

### Post by IcemanV9 on 2007-03-01
Just simply uncomment hiddenmenu in menu.lst file. You won't see it anymore until you press 'ESC' to see the menu again.

---

### Post by kindafunnylookin on 2007-03-01
Thank all three of you.
PK

---

