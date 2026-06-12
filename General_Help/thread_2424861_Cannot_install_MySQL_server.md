---
title: "Cannot install MySQL server"
date: 2019-08-15
forum: General Help
---

### Post by qajaq on 2019-08-15
I've recently switched from Kubuntu (after about 8 years of using it) to Lubuntu 19.04. Mostly, it's running well. The exceptions are the LAMP packages. I tried installing via the tasksel utility, got an error message as it was attempting to install the mysql-server package. I cleaned up the aborted mysql-server installation with ```
apt purge mysql-server mysql-server-5.7
``` and tried installing the package directly via ```
apt-get install mysql-server
``` Same result.

The error message shows up as:> ERROR: Unable to start MySQL server:
mysqld: Can't read dir of '/etc/mysql/conf.d/' (Errcode: 2 - No such file or directory)
mysqld: [ERROR] Fatal error in defaults handling. Program aborted!
Then follow some additional lines intended as helpful hints, but none proved helpful.

After the aborted installation, I looked at the **/etc/mysql** subdirectory and found no **/etc/mysql/conf.d/** subdirectory, but I did find **/etc/mysql/mysql.conf.d/**. I took a chance and renamed the file to what the installer appeared to be wanting (**/etc/mysql/conf.d**), then tried ```
apt-get --fix-broken install
``` as suggested in the installer's failure notice. The installation failed again, this time complaining that it couldn't find **/etc/mysql/mysql.conf.d/**.

So it seems that both subdirectories are wanted by the installer, but only one is being created by the installation process. What am I missing?

---

