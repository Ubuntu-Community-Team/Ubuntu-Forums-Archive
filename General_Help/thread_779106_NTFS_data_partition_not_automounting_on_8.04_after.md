---
title: "NTFS data partition not automounting on 8.04 after clean install."
date: 2008-05-02
forum: General Help
---

### Post by RCC2k7 on 2008-05-02
I had installed Ubuntu 8.04 when it was in beta, and kept updating it through the release candidate and final release. I didn't have this issue back then but I decided to reformat and do a clean install from the 8.04 Release CD to try to fix other issues. Not only I still had the issues I was trying to avoid, but now I have a new issue with this "clean install."

I have a dedicated partition for my files. (/home is useless to me since I multiboot and I'm not changing that.) This is an NTFS partition and I didn't have issues with it when I had the beta, upgraded to RC, upgraded to final release. 

But now on this clean install, the partition is not automounted. When I go to the Places menu and select the drive, nothing happens on the first try though behind the scenes I think that's when the partition gets mounted. I have to select the partition again before I can access my files. I like this approach for my XP and Vista system partitions since normally I don't need to access these within Ubuntu. But the data partition is a must-have since I set OpenOffice to look for documents there and Rythmbox's media library is on that data partition as well.

How to I get the partition to be available right from the start on Ubuntu 8.04 release, as was the case with the earlier builds?

---

### Post by ben2talk on 2008-05-18
Same problem here. I would advise you to first make sure that you copy your fstab file as it is now, and rename the copy 'fstab_original'. It is a problem I made worse with 7.10 and now am fairly happy that it's clean and that I can now manually mount everything, but automount by editing fstab is rather technical and the guides aren't working for me!

---

### Post by strabes on 2008-05-18
RCC2k7:

Please paste the output of the following commands with the drive plugged in:```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by huczek on 2008-05-24
```
sudo fdisk -l
cat /etc/fstab
```
the code doesn't add anything to fstab. i also use ubuntu 8.04.
Try method described by bsmanian in [the thread]("http://ubuntuforums.org/showthread.php?t=766688&page=2").

---

