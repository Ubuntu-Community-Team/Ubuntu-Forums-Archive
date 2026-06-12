---
title: "Change boot sequence"
date: 2016-12-27
forum: General Help
---

### Post by waltwin on 2016-12-27
I have Windows 7 ultimate and UBUNTU 14.04 installed on my hard drive. I want to change the menu so that Windows is first on the list and UBUNTU is last. There seems to be some information on how to accomplish this which I read but it is well above my pay grade.  Can someone tell me how to do this. Thank you in advance.

waltwin

---

### Post by Keith_Helms on 2016-12-27
Here's a good writeup
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

The easiest approach is to edit /etc/default/grub and change GRUB_DEFAULT=0 to GRUB_DEFAULT=1.  That won't change the displayed order in the grub menu, but it WILL change the default OS.  Do you care which OS is listed first, or just which OS is booted when you hit enter?

---

