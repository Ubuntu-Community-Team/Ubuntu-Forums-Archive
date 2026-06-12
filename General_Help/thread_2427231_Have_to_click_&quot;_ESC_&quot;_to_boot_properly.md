---
title: "Have to click &quot; ESC &quot; to boot properly"
date: 2019-09-19
forum: General Help
---

### Post by venomx2 on 2019-09-19
Installed Ubuntu all fine.
After I did an update, when I boot the PC it just goes to a black screen unless I click ESC over and over again

So basically I can only boot ubuntu by pressing escape multiple times.

I'm new to linux and ubuntu so please be basic

Thanks

---

### Post by oldfred on 2019-09-19
What brand/model system? What video card/chip?

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by venomx2 on 2019-09-19
Dell Inspiron
ATI 5450 HD

This is the problem I was getting
&#8220;A start job is running for hold until boot process finishes up&#8221;

---

### Post by KBD47 on 2019-09-19
> **venomx2 said:**
> Dell Inspiron
ATI 5450 HD

This is the problem I was getting
&#8220;A start job is running for hold until boot process finishes up&#8221;

Use blkid in terminal to determine the UUID of your  swap partition. 

Find the one that doesn't match your /etc/fstab and remove it using a text editor to put the correct UUID's into /etc/fstab and save it.

Run sudo update-initramfs -u

---

