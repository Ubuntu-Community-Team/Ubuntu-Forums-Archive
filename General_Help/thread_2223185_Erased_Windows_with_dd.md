---
title: "Erased Windows with dd"
date: 2014-05-09
forum: General Help
---

### Post by danielcasellasabdala on 2014-05-09
Hello guys, today i was trying to install Kali Linux on my computer, i was on ubuntu, and i used the dd command to write the iso to my pendrive, i accidentally wrote it to my Windows 8 Hard drive, and now i cant boot on windows 8, now i t says the hard drive is 3gb size it was 500 before T.T ... and i dont know what to do.
Thanks.

---

### Post by HermanAB on 2014-05-09
You may be able to recover some files using ddrescue.  Boot from a live CD/USB for that.

---

### Post by drac-noc on 2014-05-10
OK.... a little confusion here. Are you trying to remove Win8 and install Kali, or were you trying to install them side-by-side (AKA dual-boot)?

---

### Post by oldfred on 2014-05-10
It will depend a lot on what was in first 1GB of hard drive. Some Windows installs have recovery partition so Windows may be ok. But you probably erased partition table and efi partition.

gpt does have a backup partition table at the end of the drive.
What does gdisk say. I may offer to recover partition table from backup?

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Using live installer:
sudo apt-get install gdisk


One of the main reasons not to use the dd command as dd is extremely powerful and therefore dangerous. And some systems change drive order when flash drive plugged in which can confuse things.
       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by danielcasellasabdala on 2014-05-10
Ok, thanks for the replies, right now i made a backup image of the disk, and im trying out testdisk to see whatsup... ill see what can i get back with this and report back if it worked.

---

### Post by monkeybrain20122 on 2014-05-10
Why use dd when there are plenty of ways to write an iso? And if you have to use a dangerous tool make sure you know what you are doing. :)

---

### Post by nknwn on 2014-05-11
Which computer is this? As someone above suggested there might be a recovery partition. It might only be a case of pressing F12 on Startup to reach the recovery options.

---

