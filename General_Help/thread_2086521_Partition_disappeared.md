---
title: "Partition disappeared"
date: 2012-11-21
forum: General Help
---

### Post by hateme on 2012-11-21
Hey, guys! I searched the internet for people with my problem, but I didn't find anyone with exactly the same problem as me. So last night I installed Ubuntu on a seperate partition then Win7. I have one for win (C://), one for my own files, games, etc. (M://) and made another one (F://) just to try Ubuntu. However, after I installed it and logged in to Windows again I coundn't see my M drive with all my files and other things. I didn't format it and it is still ntfs, but I can only see it in Ubuntu. How do I fix that?? And also when I go to  Start Menu>Manage>Disk Management it shows the partition but with no letter and the only available option is to delete it...

---

### Post by raja.genupula on 2012-11-21
ok run this script and post the result here .
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by hateme on 2012-11-21
These are the results. I attached the text file.
Edit:  The missing partition should be sda5. In one of the lines it says "Linux swap / Solaris" . But when I was installing Ubuntu I didn't set it as swap space, I just clicked to not use it.

---

### Post by raja.genupula on 2012-11-24
Hi 
while doing the installation what option you choose  ?  I mean among 4 options before the partition process .

---

### Post by oldfred on 2012-11-24
Can you boot into your Ubuntu? It looks like you have no swap enabled. If you boot a liveCD it may use swap to speed things up and overwrite your sda5.

Swap is just unformatted space, but system writes RAM data to it, so if used it will overwrite existing data.

If unused you may be just able to change back to NTFS with Disk Utility. See if you can change partition type to 07 which is NTFS.

---

