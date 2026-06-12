---
title: "I want to re install windows, how will it affect my Ubuntu?"
date: 2013-04-17
forum: General Help
---

### Post by Mahrio on 2013-04-17
I want to re install windows 8 on my windows 8 partition. i currently have ubuntu 12.10 (not wubi) dualboot
all help is appreciated

---

### Post by Vaphell on 2013-04-17
reinstall how? from install disk or from recovery partition?
I have no experience with win8 but usually ordinary install of windows system makes windows take control over boot process. In such a case grub menu needs to be restored from linux livecd/usb so linux controls it and you get to access both systems.
Afaik recovery from recovery partition resets the disk to the initial out-of-factory state, which means wiping everything and leaving only fresh system.

---

### Post by Mahrio on 2013-04-17
i'm gunna download the windows 8 installer online, how do i reset the grub in 12.10

---

### Post by oldfred on 2013-04-18
Is this a Windows 8 your installed with BIOS/MBR or vendor pre-installed with UEFI/gpt. Makes a big difference.

If BIOS:
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If UEFI or BIOS:
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mahrio on 2013-04-18
alright, thanks guys. One more question, how do i back up all my ubuntu data, such as software, desktop, settings, EVERYTHING, and transfer it to another ubuntu. I might also re install ubuntu but dont want to lose all my stuff

---

### Post by oldfred on 2013-04-18
Most of your data and user settings are in /home, so you want all of that. If you manually made any hardware settings those would be in /etc. And if you installed a lot of applications, you can make a list to easily reinstall those.

 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

You do not need a lot of the temporary files or caches.

 Some files to exclude from /home backup:
[URL="http://ubuntuforums.org/showthread.php?t=1883834"]http://ubuntuforums.org/showthread.php?t=1883834

[/URL] discussion of alternatives/strategy backups
[URL="https://help.ubuntu.com/community/BackupYourSystem"]https://help.ubuntu.com/community/BackupYourSystem
      [/URL]
 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)

If you want the full image backup best to houseclean first.


    [URL="https://help.ubuntu.com/community/BackupYourSystem"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=1883834"]
[/URL]

---

### Post by Mahrio on 2013-04-19
alright, so if i want to transer my ubuntu stuff, i just copy paste the one from my current ubuntu into the new one?

---

