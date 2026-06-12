---
title: "Question about bootloader"
date: 2007-10-03
forum: General Help
---

### Post by jingdejun on 2007-10-03
I installed Ubuntu 7.10 beta on my Lenovo T61 laptop, which has 3 partitions on one physical hard driver:
C: NTFS WinXP Pro
D: Ext3 Ubuntu
E: FAT32 

I installed XP first on partition C, then install Ubuntu on partition D. 

Now I have a few questions for boot loader:

(1) During Ubuntu installation I accept the default (hd0) as the 'device for boot loader', so the boot loader is installed on MBR, right?

(2) In case of I re-install XP on partition C, will I have problem to start Ubuntu? If so, how shall I fix that?

(3) If I do not want to install boot loader on MBR, instead I install it on root partition of Ubuntu, shall I use (hd0,1) as the 'Device for boot loader' ?  

(4) If boot loader is installed on root partition of Linux (not on partition C), then when I re-install XP, will I still have problem to start Ubuntu?

Sorry I am newbie to Linux, please forgive me on these simple questions.

---

### Post by scruff on 2007-10-03
> **jingdejun said:**
> I installed Ubuntu 7.10 beta on my Lenovo T61 laptop, which has 3 partitions on one physical hard driver:
C: NTFS WinXP Pro
D: Ext3 Ubuntu
E: FAT32 

I installed XP first on partition C, then install Ubuntu on partition D. 

Now I have a few questions for boot loader:

(1) During Ubuntu installation I accept the default (hd0) as the 'device for boot loader', so the boot loader is installed on MBR, right?

(2) In case of I re-install XP on partition C, will I have problem to start Ubuntu? If so, how shall I fix that?

(3) If I do not want to install boot loader on MBR, instead I install it on root partition of Ubuntu, shall I use (hd0,1) as the 'Device for boot loader' ?  

(4) If boot loader is installed on root partition of Linux (not on partition C), then when I re-install XP, will I still have problem to start Ubuntu?

Sorry I am newbie to Linux, please forgive me on these simple questions.

#1 - Correct
#2 - Just boot from the LiveCD, chroot into your Ubuntu partition (man chroot), and do 
```
grub-install
```
That will re-install Grub as the bootloader. Anytime you re-install XP (at least once a year, right? ;) ) it will blow Grub away and you'll need to put it back. Microsoft doesn't like Windows to play nice with alternative OS's.
#3 - Not sure actually. I hate Grub's config and generally use LILO.
#4 - See answer to #2

---

### Post by scruff on 2007-10-03
Perhaps as you are a self proclaimed newbie, I should elaborate on the answer to #2. 

Boot from the livecd, open a terminal, and issue a 'mount' command (might have to sudo it - sudo mount). If the livecd allows you to become root, just do 'su' and become root (sorry I dont remember if it does). Find the mount point of your Ubuntu install. Should be something like /media/sda2 or the like. Then use the chroot like:

chroot /media/sda2 /bin/bash

Once you're in, run the 'grub-install' command and you should be all set.

---

### Post by jingdejun on 2007-10-03
Wow, thank you so much, Scruff.

Save this thread for future when I need to re-install XP.

---

### Post by MarkieB on 2007-10-04
#4 

I think the boot loader would be installed on the MBR, not on partition c, either way; as I understand it there are several 'stages' of grub, stage 1 is either a) in the MBR - as the primary bootloader, or b) in the ubuntu partition - as a subsequent chainloader [with say the windows bootloader in the MBR], either way then the later stages of grub are in the ubuntu partition; say grub is in the MBR as the principal bootloader, it may 'chainload', direct the boot to the [later stages of the] windows bootloader in partition c

clear as mud?

see eg [http://www.xs4all.nl/~lennartb/bootloaders/node3.html](http://www.xs4all.nl/~lennartb/bootloaders/node3.html)

---

