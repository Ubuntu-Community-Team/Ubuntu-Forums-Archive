---
title: "Mysql - Service will not start ater moving DBs"
date: 2012-11-22
forum: General Help
---

### Post by woolyg on 2012-11-22
Hi all,

I have been reading about this for a good day now, and no matter what I try, the mysql service will not restart after moving the database location. Could you please take a look at what I'm doing below and let me know where I'm going wrong?

(My comments are prefixed with **)


me@machine:~$ service mysql stop
mysql stop/waiting
me@machine:~$ sudo cp -R -p /var/lib/mysql /media/Data/mysql_data
me@machine:~$ sudo rm /media/Data/mysql_data
rm: cannot remove `/media/Data/mysql_data': Is a directory
me@machine:~$ sudo gksu gedit /etc/mysql/my.cnf
** Edit the file accordingly with "datadir = /media/Data/mysql_data*
me@machine:~$ sudo gedit /etc/apparmor.d/usr.sbin.mysqld
** Edit the file accordingly with "/media/Data/mysql_data/ r,
  /media/Data/mysql_data/** rwk,*
** commented out lines referring to old data location

me@machine:~$ sudo /etc/init.d/apparmor reload
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
me@machine:~$ sudo /etc/init.d/mysql restart
start: Job failed to start


No matter what I do, the service will not restart. Could someone (anyone!) let me know how to get around this?

Thanks!
- WoolyG

---

### Post by woolyg on 2012-11-22
..wow. Literally 5 minutes after posting, I changed the permissions on the parent folder of the new data directory, and boom, the service starts.

I hope this helps someone else out in the future. Thanks for reading.

- Woolyg :)

---

### Post by dcstar on 2012-11-22
> **woolyg said:**
> ..wow. Literally 5 minutes after posting, I changed the permissions on the parent folder of the new data directory, and boom, the service starts.


Then MARK the thread!

---

