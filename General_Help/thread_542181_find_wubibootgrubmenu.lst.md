---
title: "find /wubi/boot/grub/menu.lst"
date: 2007-09-03
forum: General Help
---

### Post by vektek on 2007-09-03
I really wanted to see what was so great about linux but i feel it isn't goung to happen for me... i trien installing ubuntu from their cd image which installed great but when i reboot it just goes straight to windows xp the i saw this wubi and thought this is what i need but this is no good either.... i guess bill gates owns me now!

i installed using wubi but when i reboot it just comes up with 
find /wubi/boot/grub/menu.lst
What the hell is a grub? isn't this a worm type creature? does this mean ubuntu has given me a virus? i am very new to this linux but i think maybe i'm too stupid to use it

---

### Post by Termy58 on 2007-09-03
Im pretty sure grub menu is the menu to pull up the OS list

But you can still get onto XP right?

---

### Post by vektek on 2007-09-04
thanks for your reply..... yes i can still get onto xp

---

### Post by minhmeoke on 2007-09-04
Grub is the bootloader through which you can choose which operating system to load (Windows or Ubuntu). Can you go into Windows and post the contents of C:\wubi\boot\grub\menu.lst (if you installed on a different drive, replace C: with the drive's letter) here? Check this post for more details: [http://ubuntuforums.org/showthread.php?t=538676]("http://ubuntuforums.org/showthread.php?t=538676")

---

### Post by Shirleycakes on 2007-09-13
I had this same problem and was about to post my own results when I came across a thread discussing problems with SATA drives. 

When I tried installing on my barely used IDE drive it worked like a charm. I don't know if it's all SATA drives or just large ones, as two of mine are over 200gb. The 200gb IDE worked fantasticly.

---

### Post by Murkhanand on 2007-09-16
Hi Everyone,

Greetings.

I am struggling to install UBUNTU using WUBI for the last thre days. Every time it complete up to the stage reboot. Once I reboot and chose UBUNTU as operating system, I get the message Booting 'find /wubi/boot/grub/menu.lst" and blinking cusrsor. Nothing happens. It is really very frustrating.

I have tried alternate CD or ISO but no use.

I have three Hard Drive in my system two of these are SATA and the third is Firefly.

Will some body help?

Thanks

---

### Post by ago on 2007-09-17
Wait a few days for the new release, there is a new bootloader

---

