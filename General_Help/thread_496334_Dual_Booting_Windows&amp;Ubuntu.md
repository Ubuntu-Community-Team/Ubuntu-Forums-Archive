---
title: "Dual Booting Windows&amp;Ubuntu"
date: 2007-07-09
forum: General Help
---

### Post by Tekovro on 2007-07-09
i want to know how i can get the option to choose which os i boot in. i formated my ubuntu using ext3. what would i write in the boot.ini file? in order for me to see both OS in the boot?

---

### Post by fredj on 2007-07-09
First install windows but leave some space free on your disk drive for Ubuntu. Then install
ubuntu and tell it to use the free space. It should automatically create a boot menu that includes
windows.

---

### Post by loserboy on 2007-07-09
if you originally had windows on the computer and then installed Ubuntu, assuming you didn't overwrite windows when you installed, when you bootup you should be able to choose which OS to start in the GRUB menu.

edit:  oh wait  are you saying you want to install windows after installing ubuntu? thats different altogether, as I don't think the NT loader thing can do it

---

### Post by Kodfish on 2007-07-09
post 'sudo fdisk -l' please

---

### Post by Tekovro on 2007-07-09
> **loserboy said:**
> if you originally had windows on the computer and then installed Ubuntu, assuming you didn't overwrite windows when you installed, when you bootup you should be able to choose which OS to start in the GRUB menu.


you hit the money. yeah i had ubuntu installed after i had vista installed. but i decided vista was not worth using at this point so i switched back to xp. i use windows for gaming, photoshop, bittorrent. otherwise i would always use ubuntu. before i had the option to choose when i had vista & ubuntu

---

### Post by Tekovro on 2007-07-09
[QUOTE=Kodfish[/QUOTE]

if governments were afraid of their people, they wouldn't be capable of governing.

---

### Post by Turboaaa2001 on 2007-07-09
LOL I have\had the same problem.

I installed Ubuntu then XP. The NT boot loader took over and because Windows is a loner. Anyway I had to re-install GRUB and add XP to the boot list. (I have yet to add XP to the boot list, I only need it to play high-end games and right now I dont have time)

Here is the thread: [http://ubuntuforums.org/showthread.php?t=489044](http://ubuntuforums.org/showthread.php?t=489044)

---

### Post by fumduck on 2007-07-10
here you go.. this shouold  reinstall grub so you can acess both

Peace

[http://ubuntuforums.org/showthread.php?t=496334]("http://ubuntuforums.org/showthread.php?t=496334")

also here is a guide for dual booting

[http://apcmag.com/dualboot]("http://apcmag.com/dualboot")

---

