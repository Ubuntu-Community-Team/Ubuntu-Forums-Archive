---
title: "Strange boot behavior on HP Mini-210 (12.04)"
date: 2012-11-24
forum: General Help
---

### Post by Theremin on 2012-11-24
Hi!
Since I am way too cheap to buy new computers I borrowed a HP Mini 210 netbook from a friend and replaced his old HDD with a 60 GB SSD to speed it up a little.
It is now running ubuntu 12.04 and does so very well, but it never boots properly on the first attempt.
When starting the computer "cold" it throws an "out of disk" error and a grub rescue prompt. On rare occasions it performs even worse and says something like 
"no bootable device found".
If I try to reboot immediately after shutting it down everything works fine.


I have tried using "boot-repair" without luck (the "ata disk support" option broke the boot sequence even more and I had to reinstall grub from a live usb drive).

Am I using the repair tools wrong or is this competely unrelated to grub?
Possibly even a hardware issue?

I am thankful for any help!

---

### Post by YannBuntu on 2012-11-24
Hello

Please indicate the URL provided by Boot-Repair.

Also, make sure you have no CD, or USB or SD card connected.

---

### Post by claracc on 2012-11-25
> **Theremin said:**
> Hi!
Since I am way too cheap to buy new computers I borrowed a HP Mini 210 netbook from a friend and replaced his old HDD with a 60 GB SSD to speed it up a little.
It is now running ubuntu 12.04 and does so very well, but it never boots properly on the first attempt.
When starting the computer "cold" it throws an "out of disk" error and a grub rescue prompt. On rare occasions it performs even worse and says something like 
"no bootable device found".
If I try to reboot immediately after shutting it down everything works fine.


I have tried using "boot-repair" without luck (the "ata disk support" option broke the boot sequence even more and I had to reinstall grub from a live usb drive).

Am I using the repair tools wrong or is this competely unrelated to grub?
Possibly even a hardware issue?

I am thankful for any help!

I think it can be a hardware error. Check the cable to plug the HDD to your laptop (connect and disconnect it) or change the cable if you have other one.

---

### Post by Theremin on 2012-11-25
> **YannBuntu said:**
> Hello

Please indicate the URL provided by Boot-Repair.

Also, make sure you have no CD, or USB or SD card connected.

[URL="http://paste.ubuntu.com/1383297/"]http://paste.ubuntu.com/1383297/
[/URL] 
Also, I removed and reattached the SATA cable. 
So far 5 out of 6 boot attempts has been successful so I guess it might have helped a bit but the error is still there. 
If it doesn't get worse I can definitely live with it, but in the long run it would be slightly annoying to have to start the computer twice every time.
Thanks for your help so far.

---

### Post by personalpc on 2012-11-25
Change I/O scheduler to noop and make sure your fstab is correct

[https://wiki.ubuntu.com/MagicFab/SSDchecklist]("https://wiki.ubuntu.com/MagicFab/SSDchecklist")

---

