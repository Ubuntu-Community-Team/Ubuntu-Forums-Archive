---
title: "Boot into Kubuntu not working"
date: 2013-05-27
forum: General Help
---

### Post by SkippoGuangiacomo on 2013-05-27
I've a rather strange problem. I have successfully installed Kubuntu in a computer which has Windows as well. I have done this several time before and GRUB always set (k)ubuntu before Windows but for some reason not this time. So i have one disk and 5 partitions, sda, sda1(C, Windows), sda2 (D, Windows), sda5(/, Kubuntu), sda6(/home, kubuntu), sda7 (Swap, kubuntu). I've installed Kubuntu 3 times already specifying as a a booting partition sda first, than sda1 and then sda5, but all times after restart i get into (annoyingly) Windows. I checked the setting of the BIOS, but there is only the harddisk (and not the single partitions), which follows in order to the memory stick (which is the reason why I can install Kubuntu without getting into Windows), but I am still rather puzzled. Any suggestion in how (or whether it is necessary) to set Kubuntu earlier in the master boot record? Thank you very much!!!

---

### Post by mastablasta on 2013-05-27
GRUB will automaticly overwrite MBR if you let it.

does windows maybe have a boot partition?

---

### Post by SkippoGuangiacomo on 2013-05-27
(as far as I know) I do let GRUB do whatever it has to. There is a windows boot partition, but I am not really sure how to overwrite that. I never encountered this issue in my previous installation...

also, I do not have administrator rights in Windows, but I thought I did not need them given that I can install Kubuntu without any problem

---

