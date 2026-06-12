---
title: "HDDrive identification"
date: 2008-04-15
forum: General Help
---

### Post by dryder on 2008-04-15
Hi,

Please bear with me - explaining things can be difficult (for me) - thanks.

I install all OS' on separate hdd's. When I install, I unplug the other OS drives and only non-OS drive leave plugged in - 3 OS drives, 2 other drives - all partitioned (Ubuntiu /boot, /swap, /home). I can F12 to select which drive (OS) I want to boot into.

Assuming I am installing Hardy - I unplug Windows and Feisty drives. 3 drives still plugged in. Completed install, and the other drives plugged back in.

My questions are:
1. what files will now show the wrong drive designation (h/sd,n,n) and the wrong UUID's for the (h/sdn,n) drives?
2. How can I identify the drives and edit the files to make them correct, bearing in mind my new Hardy drive should be hd0,0 while it is booting to Hardy?
3. Are any other files affected?

Many thanks for your patience and help. I have searched and googled but nothing seems to answer how to crrect them and if in doing so it creates problems.

David

---

### Post by louieb on 2008-04-15
Hard to say. 
/etc/fstab won't have the partitions on the other drives listed  for mounting.
However there is hot plug daemon, the  partitions on the other drives may get added to etc/mtab at boot up time. If thats the case then they will mounted automatically when you try to access them.

In any case it shouldn't cause any problems.

---

### Post by dryder on 2008-04-15
Thanks for replying louieb,

I have been told in [[COLOR="Blue"]**this thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=715260"), and specifically [[COLOR="Blue"]**this post**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4486513&postcount=26") that it makes the drive identification difficult (to me as a mere human) when looking at fstab and confuses Disk Analyzer.

I just like things right in case of troubleshooting later on :)

Many thanks
David

---

