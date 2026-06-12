---
title: "Kubuntu woes"
date: 2008-02-07
forum: General Help
---

### Post by venik212 on 2008-02-07
I installed kde4 (BIG mistake!), gave up on it, and gone back to kde.  However, now the following (which were fine before) are not working:

1) The large USB external drive I have been using is no longer visible, even to sudo blkid
2) When I boot, I am told there is no image to restart, and that the system is doing a normal boot.  I then get only command line, and have to start kdm by sudo kdm start

What is going on?  How do I fix it?  I have backups on the USB drive!

Thanks--

---

### Post by neurostu on 2008-02-08
Have you tried to manually mount the HDD?

Also when you say you uninstalled KDE4, how exactly did you "Uninstall"?

---

### Post by venik212 on 2008-02-09
Actually, I did not uninstall kde4-- I just chose the regular jde from the logon menu.
I did not try to mount the hdd.  I assumed it is mounted, since when I do 
sudo kdm restart, 
it starts...

---

### Post by neurostu on 2008-02-09
One of the issues is that during the KDE4 install a setting might have been set that now has it boot into the CLI, simple commands like KDM restart or, startX should work.

---

### Post by venik212 on 2008-02-10
No-- it complains that it does not find a resume image, or somesuch thing, and therefore  kinit cannot start, and thus it does "normal boot".
A very solid operating system indeed-- allowing the user to screw it up from the GUI... ;-(

---

