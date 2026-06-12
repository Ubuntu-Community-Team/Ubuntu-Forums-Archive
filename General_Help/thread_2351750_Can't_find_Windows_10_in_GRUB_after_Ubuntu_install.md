---
title: "Can't find Windows 10 in GRUB after Ubuntu installation"
date: 2017-02-06
forum: General Help
---

### Post by mimo2727 on 2017-02-06
Hello, So the problem is all in title, minutes ago I successfully installed Ubuntu. I made a patition for it in my pc & windows is in the other one (I have two). so the problem is when I finished installation and restarted pc... Boom, windows disappeared from GRUB loader and I can only boot with Ubuntu. I really need help.

---

### Post by Perfect Storm on 2017-02-06
Grub is not my thing but have you tried: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mimo2727 on 2017-02-06
I will try it and give feedback

---

### Post by yancek on 2017-02-06
When you try boot repair, I would suggest that you select the option to Create BootInfo Summary and no try to make any repairs.  It should give you a link with the output of boot repair that you can post here which wll contain pertinent information.

Which windows version do have.  If you have 8 or 10, it is probably UEFI and if that is the case, you would have had to install Ubuntu UEFI.  If you did not, the result you got would be expected.

---

### Post by mimo2727 on 2017-02-06
Thanks guys, I solved my problem and as well I can see "memory test" things + windows 10 (loader)  by using that tool

---

