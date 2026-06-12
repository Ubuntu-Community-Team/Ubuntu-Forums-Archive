---
title: "Sudoers File corrupted - help"
date: 2007-09-05
forum: General Help
---

### Post by mrfelker on 2007-09-05
Somehow my /etc/sudoers file got corrupted so command sudo command doesn't work/

The message when using sudo apt-get update for example is:

sudo: /etc/sudoers is mode 0444, should be 0440

If needed I can copy a sudoers file from a Linux that works - like Debian.

Ubuntu is mounted  as /dev/md0 (RAID 0).

What should I do?  Do I need to reinstall Ubuntu to fix this problem?  I hope not.

Marty

---

### Post by sumguy231 on 2007-09-05
You shouldn't need to reinstall, you should be able to boot into recovery mode and do a 'chmod 0440 /etc/sudoers' from the terminal. Then type 'reboot' to restart the system.

---

