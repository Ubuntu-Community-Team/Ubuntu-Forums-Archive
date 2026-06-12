---
title: "[Solved] Ubuntu 18.04 LTS No console boot output"
date: 2018-05-06
forum: General Help
---

### Post by ship22 on 2018-05-06
Just started setting up a new system with 18.04. I'm trying to move a RAID 1 set of drives to it and I think have the SATA mucked up, because now it wont' boot. I get grub, it goes to boot, then blank screen. I tried removing spash and quiet, no change... no virtual consoles either.  How do I get the noisy boot screen?

---

### Post by Xian on 2018-05-06
Try doing an edit to /etc/default/grub file. 

You wan to be sure to COMMENT this:

```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

And UNcomment this:

```

GRUB_TERMINAL=console
```

Then update grub

```
sudo update-grub
```

---

### Post by ship22 on 2018-05-09
thank you worked perfectly!

---

