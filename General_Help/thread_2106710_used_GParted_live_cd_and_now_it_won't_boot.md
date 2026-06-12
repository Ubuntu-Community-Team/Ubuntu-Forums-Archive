---
title: "used GParted live cd and now it won't boot"
date: 2013-01-19
forum: General Help
---

### Post by JooMn on 2013-01-19
Hello, not sure if this is the right place for this question, feel free to move it!

I run Lubuntu but wanted to install Windows. So I used GParted Live CD to shrink the Linux partition and create a new Windows partition. Then I installed Windows on that partition fine and it boots. Then to get back into Lubuntu I used GParted to change the boot flag from the Windows partition to the Linux partition, but now it won't boot and says Error loading Operating System. Help? :(

---

### Post by dgharmon on 2013-01-19
> **JooMn said:**
> I run Lubuntu  ..Then I installed Windows ..  now it won't boot and says Error loading Operating System. Help? :(

[How to Restore Grub]("http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05")

---

### Post by JooMn on 2013-01-19
Got it in one, thanks dgharmon :D

to anyone else with the same problem, when the posts above says
sudo grub-install --root-directory=/mnt/ /dev/sdX  
#replace the X in sdX with your partition alphabet

remember to NOT put any numbers after sd, just a letter!

Other than that the instructions work perfectly.

---

### Post by Mark Phelps on 2013-01-20
[QUOTE=JooMn;12463986]Then to get back into Lubuntu I used GParted to change the boot flag from the Windows partition to the Linux partition .../QUOTE]
In the future, you need to know that Windows REQUIRES the boot flag to be on the partition containing the Windows boot loader files -- or it will not boot.  Linux doesn't use the boot flag -- so basically, there was no need to move it.

---

