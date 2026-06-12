---
title: "partition problem"
date: 2006-09-06
forum: General Help
---

### Post by MakkoLi on 2006-09-06
This isn't my first time installing ubuntu. I had installed ubuntu 6.0 before but this time I have installed ubuntu 6.06. I installed it on my second hard drive(slave) with the extra memory on it. I have windows xp on the first drive but everytime I boot up it loads up linux. I need it to load up windows and I have gone through the documentation and have done everything they listed. It could be the MBR, I don't know. I am looking through google, but still to no avail. I'm going to continue use google, but any help you guys are willing to offer is greatly appreciated.

---

### Post by majesticturkey on 2006-09-06
If it boots into Linux, does to take you straight to the login screen, or does it give you a GRUB (lets you choose recovery mode, memtest, etc). If it's giving you GRUB, then it's really easy to add a few lines to a file and add Windows as an option - and make it the primary choice, if you want.

---

### Post by droazen on 2006-09-06
When your computer first boots, do you see the grub OS selection screen? If not, you'll need to install grub. If you do, then your problem is likely to be that your windows xp entry in /boot/grub/menu.lst is pointing at the wrong partition.

---

### Post by MakkoLi on 2006-09-06
Ya it will let me go into GRUB and I changed the menu.lst file to default X_sequence as it said in the documentation. It still doesn't give me an option of loading into windows. Am I missing something?

---

### Post by MakkoLi on 2006-09-07
Forgot to mention that when I did the stuff in the above post I am now getting 2 ubuntu and 2 ubuntu (recovery) options.

---

### Post by MakkoLi on 2006-09-07
Forgot to mention that when I did the stuff in the above post I am now getting 2 ubuntu and 2 ubuntu (recovery) options.

---

