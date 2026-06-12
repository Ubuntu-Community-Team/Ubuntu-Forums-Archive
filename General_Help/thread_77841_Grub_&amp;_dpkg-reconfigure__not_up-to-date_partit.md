---
title: "Grub &amp; dpkg-reconfigure : not up-to-date partition table"
date: 2005-10-17
forum: General Help
---

### Post by tassou on 2005-10-17
Hello there,
When I installed ubuntu on my HDD, the partition table was the following :
0) partition hard-hidden by my bios (thinkpad, "recoverey partition")
1) /
2) /home
3) swap

So my system (and my kernel by the way) was installed on hda1.

Then I managed to unhide the hidden '0' partition, and I use now this space for the swap. So today it is :

1) swap
2) /
3) home

after fixing 1 or 2 things all went allright ...
BUT !! :)

The "debian update-grub script" (and maybe some others stuffs) STILL believe that hda1 is my '/', and each time there is a kernel or module update my menu.lst is regenerated with the incorrect partition number, and I have to manually fix it.

Any idea where to find this data and fix it at the root please ? Thanx :)

Paul

---

