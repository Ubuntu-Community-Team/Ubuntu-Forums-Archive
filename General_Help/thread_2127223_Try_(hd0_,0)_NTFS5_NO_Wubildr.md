---
title: "Try (hd0 ,0): NTFS5: NO Wubildr"
date: 2013-03-19
forum: General Help
---

### Post by menyou on 2013-03-19
I am using window 8, and was trying to download “32 bit” 12.10 on my USB drive but when it reboots, I am getting these error messages. I need step-by-step assistance to solve this problem. I thank you in advance.
 
Try (hd0 ,0): NTFS5: NO Wubildr
Try (hd0, 1): NTFS5

---

### Post by oldfred on 2013-03-19
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

---

### Post by Noted on 2013-04-13
Hey I just registered for you and I just solved my problem. 
Go simply copy the file "wubildr" to the hidden partition of win8 (100 mb) it will solve the problem.

---

