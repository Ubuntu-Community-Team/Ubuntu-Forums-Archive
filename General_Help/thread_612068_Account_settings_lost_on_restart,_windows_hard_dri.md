---
title: "Account settings lost on restart, windows hard drives not accessible, etc."
date: 2007-11-13
forum: General Help
---

### Post by Kummerpaule on 2007-11-13
Hey, i am a new ubuntu user and facing the following problem:

When i boot ubuntu it stops at a certain point, saying

not automatically fixing this
/dev/sda1

after pressing ctr+alt+del it starts ubuntu. however my profile settings are lost and i can't access my windows partitions. 

does anybody know what is wrong? i would be grateful for help :)

---

### Post by ddrichardson on 2007-11-14
I'm assuming sda1 is your windows drive? If it is then chances are there is an error that needs to be corrected from Windows scandisk.

A dirty hack to get around it is to edit /etc/fstab and put a 0 as the 6th column entry for /dev/sda1 which will disable disk checking.

---

### Post by Kummerpaule on 2007-11-15
hey, thanks for reply!

you are right: sda1 is my windows drive. i already ran scandisk but it didn't fix the problem. i found out that when i boot and get this error message, i can wait for ~30 sec and then ubuntu boots further and all profile settings are there and all hard drives accessible. 
however, i don't like to wait all the time so i will try the walk-around you suggested.

if you know another solution for this problem- i am waiting ;)

---

### Post by Sef on 2007-11-15
1) What happens if you unplug the Windows hard drive?   

2) Where is GRUB set?

---

### Post by Kummerpaule on 2007-11-15
update: sda1 is NOT my windows harddrive. i checked again and sda1 is my recovery partition. i use a notebook where windows was already installed and a recovery version is stored on a hidden partition (obviously sda1). so the problem is i cant run a scandisk on sda1 under windows (at least i couldn't find a way yet). 

1) since i use a laptop i can't simply unplug the windows harddrive.
2) and i have no idea where my GRUB is set, sorry (linux is my first boot option, in case u mean that. anyway, GRUB should be set at the default place after installing ubuntu)

---

### Post by ddrichardson on 2007-11-15
I would imagine that there is an error on the recovery partition - like you said the problem is scanning it. Most vendors use a program to prevent access to the recovery partition from Windows that can be disabled by killing it from task manager.

The reason for the delay in booting is that fsck is trying to scan it on boot, so amending /etc/fstab to prevent it being scanned is one option, the other is to use ntfs tools from Linux - although this may not be an option as recovery partitions are usually Fat32. Then again, you wont need to access this partition anyway so why not just remove it from fstab so it isn't mounted at boot?

---

### Post by Kummerpaule on 2007-11-15
i unmounted the sda1 partition. still i see the blackscreen when i boot, saying sth like checking file systems.... fsck version blabla
additionally i read sth like: not automatically fixing this ... actual boot file different from backup.

---

