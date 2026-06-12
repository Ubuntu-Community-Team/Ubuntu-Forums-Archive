---
title: "Ubuntu+Win xp on separate disks?"
date: 2007-02-19
forum: General Help
---

### Post by UbuntuUbuntu7 on 2007-02-19
Hello.

I have one disc with win xp on right now. I have a empty one allso. Can i install Ubuntu on that one and then going with dual boot in this way? Will i get the alternative to boot from either win or Ubuntu automaticly then, or is there something to think about?

---

### Post by teaker1s on 2007-02-19
yes you can what happens is we automatically remove windows master boot record (mbr) and use grub which allows us to choose ubuntu or windows at boot time

---

### Post by panosk on 2007-03-17
hi there!

i have 2 raptors on sata raid 0, with windows xp on my desktop. i want to install ubuntu on a separate single sata disk and dual boot my system.

supposed i disconnect the ubuntu drive, what happens with my xp. will it be able to boot?

---

### Post by MikeDX on 2007-03-17
well, im not sure whether grub will still allow you to boot with the second drive as the second drive is where the info wil lbe stored including where windows xp is installed to

to be honest you dont really need xp.. do you? ;)

---

### Post by panosk on 2007-03-17
swap, / and /home  will be written on the second disk (ubuntu). if i disconnect the disk there will be no grub at all.

the point is whether there is any mbr information left on the xp disk/partition to allow windows boot.

:-o surprising as it may be, sometimes they can be usefull :)

---

### Post by teaker1s on 2007-03-17
not ever getting keen but if ubuntu and grub are on master boot and you fixmbr on windows disc then in theory booting second disc from bios will result in windows booting

---

### Post by panosk on 2007-03-28
i did install ubuntu 6.10 according to the instructions of this thread: [_Dual Boot on Two Drives_]("http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot+on+separate+disks")

Now, if the sata array (windows) is disconnected linux boots just fine. windows boots really nice as well with or without the linux drive connected. if it is connected i just choose by pressing pressing F8 on my bios screen which disk i want to boot with.

but if i try to boot linux with the windows drive on i get the following screen after a long system freeze:

[B]BusyBox v1.1.3 (debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)[/B]

if i ctrl+F1 i see the following:
**ALERT! /dev/sda3 does not exist. Dropping to a shell!**

i wandered through other topics to sort things out about all i got was confusion about what is going wrong.

any suggestions? thanks in advance :)

---

