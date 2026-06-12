---
title: "can't install winxp..."
date: 2005-10-22
forum: General Help
---

### Post by hassan on 2005-10-22
well guys back again with problem.i   installed unbutu breezy badger ."clean install with no paritions. "before this i used xp pro.no wi want to install win xp pro and make parition so that i can use xp pro too.
                   i tried to install gparted but can&t insall it via add applications.
                        need your help guys so that i can install xp pro.waiting for your replies.can i boot cd in unbutu?
                  regards 
                              hassan

---

### Post by codejunkie on 2005-10-22
[quote=hassan]well guys back again with problem.i   installed unbutu breezy badger ."clean install with no paritions. "before this i used xp pro.no wi want to install win xp pro and make parition so that i can use xp pro too.
                   i tried to install gparted but can&t insall it via add applications.
                        need your help guys so that i can install xp pro.waiting for your replies.can i boot cd in unbutu?
                  regards 
                              hassan[/quote]
enable the multiverse and universe repos in your /etc/apt/sources.list file and then do ```
sudo apt-get update
```& then```
sudo apt-get install gparted
``` that should get gparted installed.

---

### Post by termin8tor on 2005-10-22
Try using QTparted instead, It's a very easy to use and powerfull program =)
(you can get it using the same method codejunkie provided.)

---

### Post by garretjax on 2005-10-22
After you repartition [highly reccomend Qparted - if you don't find it in repositories, use a knoppix CD, it has it right on there] you can reinstall winXP pro.  Next problem, how do i get back into linux; as WinXP rewrites the MBR and blows away Grub/Lilo.  This you have to get back into linux through boot disks or through your 'recovery mode' on the CD.  Once you get a terminal up you will need to mount your root file system and edit your Grub [FONT="Courier New"]menu.lst[/FONT] to add XP (Remember that grub uses Base 0 notation WRT partitions HDA3 --> HD0,2). After you edit that you need to run Grub to re install it to the MBR.  Note, its been a while since i have done this, so i am not sure if this accurate step by step. I think after mounting your root filesystem you need to move to that dir and set it to be root with chroot.  Hope this helps you.


GJ

---

### Post by RYX on 2005-10-22
Since Windows XP is very mad about other OSes being installed on the same machine - you should avoid installing Windows after installing Linux. I did that way too often and I would REALLY advise you to start again, erase your disk, create partitions as you need them (Note: WindowsXP must be installed in the first partition, create a separate /home partition for your Linux - you will be happy about that), install Windows and finally install Ubuntu (or any other Linux) ... Ubuntu installation will create a GRUB entry for booting into Windows.

---

### Post by paddyg on 2005-10-22
[QUOTE=hassan]well guys back again with problem.i   installed unbutu breezy badger ."clean install with no paritions. "before this i used xp pro.no wi want to install win xp pro and make parition so that i can use xp pro too.
                   i tried to install gparted but can&t insall it via add applications.
                        need your help guys so that i can install xp pro.waiting for your replies.can i boot cd in unbutu?
                  regards 
                              hassan[/QUOTE]

Just as RYX has said, never ever install linux before windows. Windows loader is not tolerant and will overwrite grub, so you'll never get to your linux partition again.
Windows first, then linux (and grub in the MBR).

---

