---
title: "My home folder just hangs in Ubuntu 14.04 lts"
date: 2015-08-30
forum: General Help
---

### Post by rex8 on 2015-08-30
Help!  Today when trying to access my home folder, it just says loading and never opens..It hangs and even freezes sometimes. I have to kill the process nautilus just to stop it.. Anyone have a clue why this is happening all of a sudden? I can still access the files in my home folder when I type the names in the search.. Help please. thank you

---

### Post by coldraven on 2015-08-31
If you right click on the Nautilus launcher icon and select a different folder does it still hang?
Maybe there is a corrupted file in home. According to this post you can force a file system check on re-boot
[http://ubuntuforums.org/showthread.php?t=1508294&p=9452131#post9452131](http://ubuntuforums.org/showthread.php?t=1508294&p=9452131#post9452131)

---

### Post by rex8 on 2015-09-16
I found that the problem was from a webcam screen shot program that I installed. It was taking pics every second without me knowing it and filling up my home folder with thousands of files. I tried deleting them one by one and was getting no where until I found this command /home/yourname -type f -iname "*<insert title here>.jpg" -delete  . Luckily the files all had the same 1-25 numbers at the beginning so I just ran this command 25 times, each with a different number until they were all gone.

---

