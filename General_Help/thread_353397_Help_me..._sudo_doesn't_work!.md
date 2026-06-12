---
title: "Help me... sudo doesn't work!"
date: 2007-02-04
forum: General Help
---

### Post by User-007 on 2007-02-04
Hi!

My problem:

$ sudo apt-get update
sudo: /etc/sudoers is mode 0755, should be 0440

How to fix this?

Thanks,
User JB

---

### Post by gradedcheese on 2007-02-04
boot up in recovery mode, getting you a root shell.  then:

chmod 440 /etc/sudoers
shutdown -r now

---

### Post by User-007 on 2007-02-04
thanks, cheeseguy, your help was worth of gold

---

