---
title: "Backup to Google"
date: 2018-04-27
forum: General Help
---

### Post by windowsfree on 2018-04-27
Hello,

I have just installed Xubuntu 18.04 and want to use Deja Dup to back up to Google.  I am unsure of how to configure my Google Account to work with this.
See screenshot:



Where do I go to configure the account?

Thank you for your time and response.

---

### Post by deadflowr on 2018-04-27
Normally, you would open the Online Accounts program.
But since it's a GNOME program and you are on Xuibuntu, it might not be there.
In which case you may need to install it.
try
```
sudo apt install --no-install-recommends gnome-online-accounts
```
(The no-install-recommends flag will stop it from installing the gnome control center, which I doubt you'll care for.)

Current info on gnome online accounts for 18.04:
[https://packages.ubuntu.com/bionic/gnome-online-accounts]("https://packages.ubuntu.com/bionic/gnome-online-accounts")


Hope it helps

---

### Post by windowsfree on 2018-04-28
Thank you, I have installed as you suggested, now how to I access it.  It shows installed, but how do I launch it,  i don't see it in a graphical user interface menu.

Thank you.

bob@HP3515-Series:~$ sudo apt install --no-install-recommends gnome-online-accounts
[sudo] password for bob: 




Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-online-accounts is already the newest version (3.28.0-0ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by deadflowr on 2018-04-28
Sorry, I guess you actually do need gnome-control-center to utilize the online accounts for some reason.
```
sudo apt install gnome-control-center
```
If it doesn't show, you may need to open with
```
gnome-control-center online-accounts
```
see if that gives you the right access and setup settings.

---

### Post by windowsfree on 2018-04-28
that is not working either, I guess I will just make local backups and take one off-site

---

