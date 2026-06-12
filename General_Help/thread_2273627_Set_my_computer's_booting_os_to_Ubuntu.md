---
title: "Set my computer's booting os to Ubuntu"
date: 2015-04-14
forum: General Help
---

### Post by gogor67 on 2015-04-14
Hi,

I've recently installed Windows 8.1, Ubuntu 14.04, and Kali Linux 1.1, in this order, on my hard drive, so my computer boots to the awful Kali grub automatically.
In order to change this, I've tried to compile burg on my Kali, but it has not worked. And anyway, I'm using Kali less than Ubuntu and Windows, so I'd like my computer to boot to Ubuntu first ( and then I'd install burg on ubuntu, which is quite easy ).
I' ve been spending quite a long time looking for how to do this on the web, but I usually find people asking how to change the default booting OS inside ubuntu's grub, which is not what I am looking for at all.
When I change the boot order in the BIOS settings, I cannot boot on either Windows or Ubuntu ( it says "no operating system found" ), but these 2 os work fine as I'm currently typing through Windows.

This question has probably already been asked, and I'm sorry about that, but it's pretty hard to find the answer as the key words are common.

Thanks for reading, have a good day ):P

---

### Post by pmi2 on 2015-04-14
Have you tried running Boot-Repair?  I am not sure how that will handle Kali, but in my case, it defaults to Grub on my first installed Linux version.  In other words, if Grub was changed when a second OS is installed later, running Boot-Repair resets to the earliest installed os (in my case that is Ubuntu 14.04).

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Holger_Gehrke on 2015-04-14
It always comes down to changing the grub configuration and making grub use the changed config. A short article on this for Kali linux can be found [here]("http://www.sajeeva.net/articles/change-default-boot-order-grub-kali-linux-dual-boot-system/").

---

### Post by gogor67 on 2015-04-14
Thank you guys for replying ! Holger_Gehrke, this is the kind of information I find when I'm looking for solutions, but I don't think it is what I need, because if I want Ubuntu to boot by default, I' ll have to set the default boot option to x ( x being Ubuntu' s number ) and then set the waiting for input time to 0. But if I did that, It'd start Ubuntu without letting me see Ubuntu's grub menu.

I'll try running a boot-repair live CD later, and let you guys know if it worked.

---

### Post by sotiris2 on 2015-04-14
Why can't you just set the default option to x and the waiting time to 5 (for example?) what's stopping you?

---

### Post by Impavidus on 2015-04-14
The OS that controls grub, will put itself at the top of the list. To make kernel upgrades work, it's easiest to let the most used Linux system control grub. The best thing to do is making Ubuntu in control of grub by booting Ubuntu and reinstalling grub from there.```
sudo grub-install /dev/sda
```Substitute the drive where your Ubuntu is installed. I don't know how and if you have to change this command in case of UEFI, which may be applicable to you.

I can be mistaken, but I don't see a lot of activity in the burg project. Not sure it'll be such a good idea to install burg.

---

### Post by gogor67 on 2015-04-14
@ Sotiris2, I wanted the Ubuntu GRUB menu instead of Kali's, so setting up a default option in Kali's menu would not have solved anything.

Anyways, I just found out when running a boot-repair live session that there is a super easy way to do this.
Go to advanced settings, and there' s somewhere an option called "Default booting OS". I just had to select Ubuntu there, then I applied the changes and everything seems to work fine now. Thanks for your help !

---

