---
title: "How to install Plop to boot sector instead of MBR"
date: 2015-02-04
forum: General Help
---

### Post by seeker.k3 on 2015-02-04
I have a computer with just Xubuntu on it. On top of the list of problems is the fact that I can't boot from a CD or USB (and updating the BIOS didn't change anything). Installing Plop Boot Manager would help me, I think.

The Plop website says:
[HTML]Warning Linux users: Install LILO or GRUB to the boot sector of your Linux instead  of the Master Boot Record (MBR). The Plop Boot Manager is not a Linux loader and cannot start Linux without LILO, GRUB, Syslinux and similar![/HTML]

However:
```
sudo grub-install /dev/sda
```
writes in the MBR. How do I install GRUB to the boot sector?

BTW, I can't start X, so I'm looking at tty.
Thanks.

---

### Post by yancek on 2015-02-04
I've never used Plop but I expect it just chainloads to the partition containing the boot files like a lot of these third party bootloaders.  You have Grub on the partition so where do you have plop installed, or do you?  The command below has worked for me in the past installing Grub to a partition.  If you install Plop to the mbr and it fails, your machine will be unbootable so you will need Xubuntu installation medium to repair that.   Change 'sda4' below to whatever your partition is.   

> sudo grub-install --force --root-directory=/mnt/sda4 /dev/sda4

What exactly are you trying to do.  There may be an easier and less potentially destructive way of doing it.  Boot an iso perhaps?

---

### Post by Bucky Ball on 2015-02-04
I had a similar problem on my old desktop. Changing BIOS would change the boot to CD or USB. Oddly enough, when I used F12, which takes me to a boot device selection screen, that worked fine. Never figured that one out. BIOS worked to change boot devices if I wanted to change the HDD to boot from, though. Just not disk or USB. Old box so BIOS is probably right out of date.

---

### Post by yancek on 2015-02-04
You know, you never actually explained what your problems was.  Can't boot from a CD or flash drive, were you ever able to do that?  Do you have a CD/DVD drive that is functional?  Is your computer old enough that it doesn't have the capability to boot from a usb port?  Do you have multiple usb ports?  Have you tried them all?  Have you set the CD/DVD drive to first boot priority?  Same with the flash drive?

---

### Post by sudodus on 2015-02-04
> **seeker.k3 said:**
> I have a computer with just Xubuntu on it. On top of the list of problems is the fact that I can't boot from a CD or USB (and updating the BIOS didn't change anything). Installing Plop Boot Manager would help me, I think.

The Plop website says:
[HTML]Warning Linux users: Install LILO or GRUB to the boot sector of your Linux instead  of the Master Boot Record (MBR). The Plop Boot Manager is not a Linux loader and cannot start Linux without LILO, GRUB, Syslinux and similar![/HTML]

However:
```
sudo grub-install /dev/sda
```
writes in the MBR. How do I install GRUB to the boot sector?

BTW, I can't start X, so I'm looking at tty.
Thanks.

1. Please describe what you have and what you want according to yancek's questions!

2. It seems your computer boots from an internal drive with grub. If this is the case, another option is to chainload from grub into CD or USB or a second internal drive. See the ***third post*** of this thread [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by seeker.k3 on 2015-02-06
Thank you for your help.

---

### Post by sudodus on 2015-02-06
Please share the solution with us :-)

---

### Post by C.S.Cameron on 2015-02-06
Just visited the plop site and it looks like things have gotten complicated.
(and some people accuse me of getting verbose)
I recall installing plop to the MBR and it was similar to Grub.
I had the option to boot USB flash drives, CD's DVD's and HDD's.
Have you tried to just install it to MBR, it might do what you want.

---

### Post by Bucky Ball on 2015-02-06
> **sudodus said:**
> Please share the solution with us :-)

This. The way things are done here. Please share with the community what worked to help fellow travelers. ;)

---

### Post by seeker.k3 on 2015-02-08
[FONT=arial]My apologies for the delay. Getting this computer sorted out has been long and, to be honest, clumsy process. 

Based on the comments here, I didn't attempt Plop. The solution was sudodus' chainloading with the 40_custom method,  suggested in post #5 above---follow the link.

The computer is a Dell Dimension (desktop), which probably hadn't been started for a year or two (I don't know). I found the CD and USB ports worked, but wouldn't boot, and the Xubuntu that was on there had problems: no X and couldn't complete update, and so on. I flashed the BIOS (I'm not sure now if that was necessary, but I thought so because the battery was dead), and spent some time looking at the BIOS settings. Perhaps it was that FAT was not recognised? I haven't thought more about the CD, I don't need to now.
[/FONT]
[FONT=arial]Editting /etc/grub.d/40_custom[/FONT] certainly worked in that it failed in a very promising way. After that, UNetbootin didn't work, but USB Disk Creator did. I haven't yet installed Xubuntu, but Live works, so it clearly will install. That's the next step.[FONT=arial]

Again, I apologize for my rudeness. Other things have been occupying me in recent days.[/FONT]
Cheers. :)

---

### Post by sudodus on 2015-02-08
Thanks for sharing your steps to a solution :KS

Please create a new thread with a good descriptive title, if you need help to install and make Xubuntu work well! In that case you can post a link here to that new thread. This way more Xubuntu users will read your thread and be able to help.

---

