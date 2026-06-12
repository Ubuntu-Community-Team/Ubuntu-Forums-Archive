---
title: "clonezilla error"
date: 2012-11-10
forum: General Help
---

### Post by dtrapp on 2012-11-10
I am trying to make a clone of an ubuntu 12.04 partition using clonezilla 1.2.8-46. I have used using this program dozens of times, but this is the first time since upgrading to 12.04.

I get this error:

[B]Starting to clone device
Reading Super Block
Calculating bitmap
Completed 97.10% , extfsclone.c: bitmapfree count error, free[/B] (screen ends)
[B]17750020 
Partclone fail, please check /var/log/partclone.log!
Checking the disk space...
(standard_in) syntax error[/B]

I cannot find the partclone.log file
I am able to make a clone of a windows partition. 
Thanks for the help

---

### Post by dtrapp on 2012-11-17
For anyone that's interested, the problem has been fixed. I encountered the problem in Clonezilla 1.2.8-47. I downloaded the latest version of 1.2.12-63 which offers a menu which allows the users to correct file errors, which I did. It turns out that I apparently had an error between the # of free count cell clonezilla saw and what the system reported.

---

