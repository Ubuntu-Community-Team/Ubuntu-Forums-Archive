---
title: "High CPU load in idle"
date: 2007-12-26
forum: General Help
---

### Post by OkeyuL on 2007-12-26
Hi all.

The problem is that in idle, one of the CPU is at about 30% all the time.
This is comming from **ksoftirqd**.

Solution (found on the internet, not mine):
 - edit boot options:
   **sudo nano /boot/grub/menu.lst**

 - add at line that starts with "# kopt=":
   **nohz=off**

 - close and save

 - update configuration with:
   **sudo update-grub**

 - reboot

PS: Ubuntu 7.10 64bit, proc Intel

---

### Post by lisati on 2007-12-26
[http://ubuntuforums.org/showthread.php?t=202595](http://ubuntuforums.org/showthread.php?t=202595)

---

