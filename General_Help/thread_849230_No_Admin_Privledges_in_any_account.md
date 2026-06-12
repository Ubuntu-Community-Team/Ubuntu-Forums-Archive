---
title: "No Admin Privledges in any account"
date: 2008-07-04
forum: General Help
---

### Post by danielgroves on 2008-07-04
Hi,

I just set my PC to Dual-boot with MS Windows XP Home Edition and Ubuntu Linux 8.04 Desktop.  I kinda mucked up when setting up accounts for other users as I now have no Admin privileges on the admin account, or on any of the other accounts.  How do I fix this????

---

### Post by sisco311 on 2008-07-04
Reboot your computer in Recovery Mode(Select it from the grub menu).
and execute this commands from the root shell
```
addgroup *username *admin
exit
```replace username with your user name
select the resume normal boot option from the menu.

---

### Post by danielgroves on 2008-07-04
Thanks sisco311, it worked perfectly!

---

