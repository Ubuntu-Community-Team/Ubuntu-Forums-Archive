---
title: "need to reinstall GRUB"
date: 2008-04-07
forum: General Help
---

### Post by FastMady123 on 2008-04-07
I have a problem. I can't boot Windows XP and/or Ubuntu. GRUB won't boot. It got an error. The error is "Error 17". I try to use code to reinstall GRUB but it too hard to do it. I can't use Super 
GRUB Disk becuase I don't have a blank CD to burn. I want to be done by the end of the week. I don't have Internet access for my laptop because i9'm staying at someone's home and they all are using wireless and I need to use wire becuase I using the LiveCD. I'm using a laotop. My laptop has Windows XP and Ubuntu. What should I do?

---

### Post by c_07 on 2008-04-07
Have your tried re-installing GRUB using the method [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")?

---

### Post by dstew on 2008-04-07
Boot the Live CD. Open a terminal window (Applications --> Accessories --> Terminal). On the command line enter```
sudo fdisk -l
```(If it asks for a password, just hit return). This will give you a print-out of your disk partitions. Post this list to the forum.

Do you get an error message with the Error number, like "Cannot mount selected partition", or is it just "Error 17" all by itself?

---

### Post by FastMady123 on 2008-04-07
> **dstew said:**
> Boot the Live CD. Open a terminal window (Applications --> Accessories --> Terminal). On the command line enter```
sudo fdisk -l
```(If it asks for a password, just hit return). This will give you a print-out of your disk partitions. Post this list to the forum.

Do you get an error message with the Error number, like "Cannot mount selected partition", or is it just "Error 17" all by itself?

It has nothing to do with partitions.

---

### Post by dstew on 2008-04-07
> It has nothing to do with partitions.Why do you say that? The error is caused by grub being unable to mount the partition you installed as its root. The answer is to re-install grub. I was going to help you do this, but we need to know which partitions are in your computer to make sure we install grub correctly.

---

