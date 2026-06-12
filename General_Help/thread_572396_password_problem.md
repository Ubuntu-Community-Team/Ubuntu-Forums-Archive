---
title: "password problem"
date: 2007-10-10
forum: General Help
---

### Post by hraposo on 2007-10-10
I've a servidor with ubuntu 5.10, but than ehen I try to do login it don't accept the password How can I restore the password ore define another one?

How can I solve this problem?

---

### Post by #Reistlehr- on 2007-10-10
If i understood this question correctly..

for the root password, if you need to reset it, you can select Recovery Mode in the GRUB bootloader screen, and when it comes to the terminal, type, 

passwd root

and then put in the new password, reboot, and you're off.

---

### Post by marticus on 2007-10-12
hi great tip also works for resetting your user password which is what i did 
i booted to the recovery console and used passwd (username) which allows you to reset your password 

not much but thought id add it any way

---

