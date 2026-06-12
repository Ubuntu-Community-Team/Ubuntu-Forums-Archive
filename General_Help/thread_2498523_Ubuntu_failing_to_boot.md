---
title: "Ubuntu failing to boot"
date: 2024-06-17
forum: General Help
---

### Post by onlytherealest on 2024-06-17
Hello,

Yesterday I rebooted my laptop and now it refuses to boot. I have an ASUS Vivobook with dual boot (Ubuntu 22/Windows 10; I rarely use the Windows partition). I've tried troubleshooting using recovery mode. I tried all of the options in the menu as well as updating all my packages, and reinstalling the desktop. This didn't fix it. Today I got a live USB and tried running fsck as well as boot-repair, but it still doesn't work. Here is the paste from boot-repair: [https://paste.ubuntu.com/p/drHMk67bFc/](https://paste.ubuntu.com/p/drHMk67bFc/)

Here is a photo of what Ubuntu says when trying to boot: [IMG]https://ubuntuforums.org/attachment.php?attachmentid=293879&stc=1[/IMG]

The '/dev/nvme0n1p4: ******/******** files. ********/********* blocks' message has appeared consistently. I'm not very fluent in troubleshooting, and I can't think of any more things to do. What can I do to recover?

---

### Post by oldfred on 2024-06-17
You are booting past grub, so Boot-Repair will not fix issue.
What is in USB3 port 2?
lsusb
Lots of detail
lsusb -vvv
Or detail on one device using info from lsusb.
Details on one port, first number is bus, second is device:
lsusb -v -s 3:3

---

### Post by onlytherealest on 2024-06-17
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293880&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293881&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293882&stc=1[/IMG]
These are the outputs I get, some issue with my bluetooth.

---

### Post by oldfred on 2024-06-17
Please do not post screen shots of terminal output.
Copy & paste & use Code tags, easy to add with Go Advanced editor & # icon.
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]

I turn Bluetooth off on my system as I do not use it. So not familiar with issues.

---

### Post by onlytherealest on 2024-06-18
For anyone seeing this in the future, I fixed this by reinstalling and purging xorg. This fixed my booting issue. After that I had keyboard issues that I fixed with 'xorg :1 -configure'.

---

