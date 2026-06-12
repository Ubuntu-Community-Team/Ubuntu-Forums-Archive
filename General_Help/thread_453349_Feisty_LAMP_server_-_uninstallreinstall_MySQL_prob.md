---
title: "Feisty LAMP server - uninstall/reinstall MySQL problems"
date: 2007-05-24
forum: General Help
---

### Post by adamscottmartin on 2007-05-24
I am a linux newb but I am getting the grasp very quickly. However I made a mistake today on my test server and I have no idea how to fix it w/o a drive wipe/OS reinstall. I am sure that someone will have a fairly simple answer...

So basically I installed phpMyAdmin to work on MySQL. I then proceeded to accidentally delete all root users from MySQL when configuring priveledges for them (I was trying to set a password for root after initial installation but instead dumped all root users). At this point I couldn't log into MySQL so I figured I needed to reinstall.

After some Google searching, I found that I should type dpkg --purge mysql-server (supposedly). So I did. Then I reinstalled MySQL server (after a quick su) using 'apt-get install mysql-server'.

I still cannot get into MySQL through phpMyAdmin using user=root, pass=<blank>. I am not sure if something isn't installed properly for MySQL or how to check it.  I have the feeling I need to remove all MySQL services and then install them again, but I don't know the exact commands or all the packages I need to remove/apt-get again, or if there is a simpler way maybe?

Any ideas?

---

### Post by Viskovitz on 2007-05-24
Have you tried [resetting]("http://www.megalinux.net/archives/183.html") the root password?

---

### Post by adamscottmartin on 2007-05-24
As I said in my original post I accidentally deleted all instances of the root user.  It doesn't seem like MySQL server is working correctly either even after I did the apt-get for mysql-server but I can't be sure because I don't know how to check.

---

### Post by strixy on 2007-05-24
When logging into MySQL using phpmyadmin, try using your system root password instead of leaving it blank.

If that doesn't help

Try using synaptic to **completely remove** MySQL. (Which will also remove any data, database files, configuration files, etc...)

Then reinstall MySQL and try again with the system root password instead of <blank>

---

### Post by az on 2007-05-24
> **strixy said:**
> When logging into MySQL using phpmyadmin, try using your system root password instead of leaving it blank.

If that doesn't help

Try using synaptic to **completely remove** MySQL. (Which will also remove any data, database files, configuration files, etc...)

Then reinstall MySQL and try again with the system root password instead of <blank>

The system root and the mysql root are completely different!  You are not required to have root priviledges to run mysql or administer the mysql root user.

See here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If you run

mysql -u root

what happens?

---

