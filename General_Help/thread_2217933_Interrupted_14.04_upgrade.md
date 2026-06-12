---
title: "Interrupted 14.04 upgrade"
date: 2014-04-18
forum: General Help
---

### Post by clementchiew on 2014-04-18
I interrupted my 14.04 (from 13.10) upgrade because my computer froze.  So i could not boot into Ubuntu. Using Live CD, I tried a guide online  to fix. [http://ubuntuforums.org/showthread.php?t=1920317](http://ubuntuforums.org/showthread.php?t=1920317) 

The thing is, when i rebooted my computer after upgrading, I cannot  enter boot screen. After Grub, selecting normal boot puts me in a empty  screen with a blinking underscore for a long time. Trying failsafe  graphics mode does not work. It sends me back to recovery screen. Help please.

---

### Post by carl4926 on 2014-04-18
Would it be easier to do a clean install of 14.04 ?

---

### Post by clementchiew on 2014-04-18
I was already using 13.10 prior upgrading and I have important files. I am not shifting from another distro or from XP. Now I cannot access my files.

---

### Post by carl4926 on 2014-04-18
You didn't backup before the upgrade? It's a given...

---

### Post by oldfred on 2014-04-18
What video card/chip do you have.

Did you install proprietary drivers or any ppa's?  Most find upgrades work well if all proprietary drivers and ppas are removed before an upgrade.

Can you boot in recovery mode? 
Or with nomodeset or whatever boot parameters your model system needs?

---

### Post by clementchiew on 2014-04-19
AMD HD Radeon Mobility 4570. 

No I didn't. Neither are there any proprietary drivers for my card. 

I cannot boot in recovery mode. As mentioned, after my selection in Grub, it gives me an empty black screen with a blinking underscore. I can type stuff but it is irresponsive to commands like shutdown now. I tried booting with an older kernel and still didnt work. 

I don't really understand your last question. sorry. :/

---

### Post by carl4926 on 2014-04-19
> **clementchiew said:**
> AMD HD Radeon Mobility 4570. 

No I didn't. Neither are there any proprietary drivers for my card. 

I cannot boot in recovery mode. As mentioned, after my selection in Grub, it gives me an empty black screen with a blinking underscore. I can type stuff but it is irresponsive to commands like shutdown now. I tried booting with an older kernel and still didnt work. 

I don't really understand your last question. sorry. :/

Is the kernel in the menu for 14.04?
Have you tried to chroot in to your system?

---

### Post by kowloon2 on 2014-04-19
You can try boot-repair (boot from CD or USB with boot-repair in it).

---

### Post by Elfy on 2014-04-19
> **kowloon2 said:**
> You can try boot-repair (boot from CD or USB with boot-repair in it).

boot-repair is not available for 14.04 yet, would need to change the source file to point at saucy

---

### Post by sdowney717 on 2014-04-19
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

why not download, then use unetbootin to create a bootable usb drive.

then boot this and it can fix your boot issue.

Also, if you can boot to a command prompt with networking, you can run 
sudo apt-get dist-upgrade

I have used this to repair boots with Trusty 14.04

---

### Post by monkeybrain20122 on 2014-04-19
Well the upgrade shouldn't have damaged your data files in /home. Boot off a live usb to retrieve them and then erase everything and do a clean install. You won't have to go through all these troubles if you just backed up your files and took 20 minutes to do a clean install. "Upgrade" is complex and fragile, it is not a very reliable process and takes a very long time. I wish they give people more warnings and education instead of having a popup pushing people to upgrade.

---

### Post by kowloon2 on 2014-04-19
Sorry, if he have other computer to use, he can download boot-repair and burn to CD. 
[http://sourceforge.net/projects/boot-repair/](http://sourceforge.net/projects/boot-repair/)

---

### Post by kowloon2 on 2014-04-19
> **sdowney717 said:**
> [http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

why not download, then use unetbootin to create a bootable usb drive.

then boot this and it can fix your boot issue.

Also, if you can boot to a command prompt with networking, you can run 
sudo apt-get dist-upgrade

I have used this to repair boots with Trusty 14.04

I totally agree with you (sdowney717).  I've used similar procedure after I upgraded to 14.04. [SIZE=4][COLOR=#000000][/COLOR][/SIZE]

---

