---
title: "Something in Grub changed."
date: 2012-10-22
forum: General Help
---

### Post by moteprime on 2012-10-22
On my Ideapad s205 the efi bios are made to boot windows, if there are no windows booter it will use a backup windows booter, which makes it a bit bothersome to install Ubuntu (in dual boot).
With Oneiric and Precise the solution was to install EasyBCD bootloader, (in windows) and point it to grub.
The Ubuntu installation process detected that the laptop has a efi bios so it installed a efi version of grub that does not work with the EasyBCD program (or the bios), so after installing Ubuntu I did this from live session to install “grub-pc” instead.
sda5 250mb /boot and sda6 350Gb /

```
sudo su
mkdir /mnt/sda6
mount /dev/sda6 /mnt/sda6
cd /mnt/sda6
mount /dev/sda5 ./boot
mount --bind /sys ./sys
mount --bind /proc ./proc
mount --bind /dev ./dev
chroot .
apt-get update ; apt-get install grub-pc
```

But in Quantals grub something has changed so the EasyBCD program can not find grub and start it up?
As a workaround I have installed Precise on a small partition and uses its grub to startup Quantals grub.
But taking two extra steps is a bit silly I think.
windows &#8594; Precise &#8594; Quantal

What changed in grub, and how do I get a regular grub installed. (not legacy)?
Thanks

---

### Post by oldfred on 2012-10-22
If you have MBR partitioning for BIOS boot it should not have installed in UEFI mode. But 64bit installer offers both UEFI or BIOS from a UEFI boot of installer. Which ever way you boot installer, is the way it installs.

Probably best to post the BootInfo report so we can see all the details.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by grahammechanical on 2012-10-22
What changed? Grub itself changed.

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")

Ubuntu 12.04 uses Grub 1.99. Ubuntu 12.10 uses Grub 2.0 and yes there are differences. Especially in how kernels are designated.

Gone is sda1, sda5, etc. In is msdos1, msdos5, etc.

Regards.

---

### Post by moteprime on 2012-10-23
Thank you both for your replies.

I did not know that Grub was upgraded and "Changed", but thank you for the information.
The base of the problem lies in the Ideapad bios that, if a Windows are present, will only boot Windows. -As far as I know.

Here are the boot-repair info:
[http://paste.ubuntu.com/1299480/](http://paste.ubuntu.com/1299480/)
I installed it, not in a live session, but on my Ubuntu on the HD.

Thank you. :-)

---

### Post by oldfred on 2012-10-23
You still have Windows in the MBR and are booting in BIOS/MBR mode even if your system has a newer UEFI/BIOS system.

You have grub2 installed to the MBR of sda5 which I think is what you have to do with EasyBCD. But grub installed to a partition is not reliable.

If you really want EasyBCD you may do better in their forum as they are more up to date.

But you want to put grub2's boot loader into the MBR, you can just use the Boot-Repair tools to fix that. Then from the grub menu you can boot any of the three systems you have installed.

Since you have two Ubuntu's you can install either install's version of grub to the MBR. Which ever you install from will be first in the menu or default and the other listed near the bottom with Windows. And you can easily change from one to the other just by booting into the one you want and reinstalling its grub to the MBR.

sudo grub-install /dev/sda

---

### Post by moteprime on 2012-10-24
I have no desire to use neither Windows or EasyBCD if i can do without it.  ;-)

-I ran the boot-repair and it worked, -it really worked!
Today i am the happiest Ubuntu user. No longer do i have to boot through the windows bootloader. The hours i, (and others) spend trying to solve this.
Thank you so much, you are a true gentleman.




PS: suspend/wakeup haven't worked since 12.04, and i don't know how to trouble shoot it. Are you able to help out with that as well? -Thank you.
[http://ubuntuforums.org/showthread.php?t=1986026]("http://ubuntuforums.org/showthread.php?t=1986026")

---

### Post by YannBuntu on 2012-10-24
Hello

> **moteprime said:**
> -I ran the boot-repair and it worked, -it really worked!

Great :)
Please could you use the Thread Tools to mark this thread [SOLVED]?

Also, please could you help translating Boot-Repair into Danish? ( [https://translations.launchpad.net/boot-repair](https://translations.launchpad.net/boot-repair) ) Thanks !

---

### Post by moteprime on 2012-10-25
> Also, please could you help translating Boot-Repair into Danish?

Yes, I will be honoured to.
Thanks.

---

