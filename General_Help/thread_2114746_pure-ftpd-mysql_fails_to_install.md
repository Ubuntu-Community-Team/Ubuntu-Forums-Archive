---
title: "pure-ftpd-mysql fails to install"
date: 2013-02-10
forum: General Help
---

### Post by patdundee on 2013-02-10
Hi Guys
Ubuntu 12.04.2 Since the update from 12.04.1 pure-ftpd-mysql fails to both remove and install

Each time i try to remove with apt-get remove --purge pure-ftpd-mysql i get 
Removing pure-ftpd-mysql ...
#

And it just hangs and dpkg gets locked and i have to reboot and issue the command dpkg --configure -a

If i then try to re install it with apt-get install pure-ftpd-mysql or apt-get install -f i get 
Setting up pure-ftpd-mysql (1.0.35-1) ...
and again it just hangs and goes no where
Any suggestions would be greatly appreciated
Many thanks
PS i have also tried the purge option and the result is still the same

---

### Post by patdundee on 2013-02-11
Hi Guys
Has any one got any ideas on this one. The issue is definately with the MySQL install and removal part. Even after trying to re install and getting stuck on the MySql file Pure FTP runs, but does not integrate with the MySql database

---

### Post by patdundee on 2013-02-11
After running dpkg --purge and apt-get autoremove --purge -s This is what is displayed if it is any help

Purg pure-ftpd-mysql [1.0.35-1]

It is always on here that the system hangs and fails to remove

---

### Post by patdundee on 2013-02-11
Hi Guys
I have solved my own issue. Though i would not recommend this, After all the un-install processes failed, i eventually gave in and manually located all the remaning files that had anything to do with pure-ftpd and removed them all manually, this then allowed the removal to complete.

Using Webmin file manager I did a search for everything that matched pure-ftpd, pure-ftpd-mysql and pure- and deleted them all. There were about 66 files still remaining.

I have since managed to successfully re install pure-ftpd

---

