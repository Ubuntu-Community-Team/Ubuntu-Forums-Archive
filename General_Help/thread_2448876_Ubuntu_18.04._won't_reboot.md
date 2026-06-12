---
title: "Ubuntu 18.04. won't reboot"
date: 2020-08-15
forum: General Help
---

### Post by martinrinconbotero on 2020-08-15
Hello,

this is not a very important issue, because I rarely have to reboot, but when I have to I'm unable to. I've read that there *could* be some configuration for the GRUB which would solve the problem. I tried already adding "nomodeset" to the GRUB, which impedes proper recognizing of my external monitor, so that's not an option. My CPU is an Intel(R) Pentium(R) CPU N4200, Asus F541N. I remember having to add a line of code somewhere after installing, so that Ubuntu wouldn't hang when shutting down, so probably both issues are connected. I never had any problem shutting down again after that fix (I think it was changing a certain time-out to 4 seconds or so), but not being able to reboot still persists. When I hit reboot, the system appears to be rebooting, I can see the ASUS logo and the system just hangs there. No purple screen or anything. I have to manually turn it off and on again. 

Any help would be appreciated.

Best regards,
Martín.

---

### Post by CelticWarrior on 2020-08-15
Welcome.

First of all update UEFI ("BIOS").

---

### Post by mikes365 on 2020-08-15
I had this problem a while ago, I just used the "sudo reboot" command and everything went great.
After updating to Ubuntu 20.04 I do not have this problem anymore...

---

### Post by martinrinconbotero on 2020-08-16
Thanks for your answers. I'll try updating to 20.04..

---

