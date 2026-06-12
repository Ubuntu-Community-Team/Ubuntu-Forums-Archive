---
title: "Help! Newbie accidently deleted /var"
date: 2007-02-10
forum: General Help
---

### Post by guest123 on 2007-02-10
I accidently deleted contents of var/ - including all subdirectories. Ubuntu boots up, but all the system fonts are replaced by empty boxes (menus, windows, etc). I do have fonts within terminal and within firefox, so I can run command-line commands but I cannot operate window interface. What packages do I need to run to reconstruct the contents of var/? I am hoping to avoid a full upgrade/reinstall for now.

I am running a dual boot system on IBM Thinkpad Lenovo laptop and this is my first Ubuntu (6.06) - I am still not very familiar with it (I am used to Red Hat).

Please help.

Please do not dwell on how stupid it was - I already dwelled on it.

Thank you.

---

### Post by gradedcheese on 2007-02-10
Hey, you picked the right directory to blow away :)  /var contains mostly run-time stuff, so a lot of it will recreate itself when you reboot (have you rebooted?).  Mainly /var/lock is needed, as is /var/log but they will be created for you I believe.  Now, please don't go and blow away /etc or /usr or /bin or /boot...

---

