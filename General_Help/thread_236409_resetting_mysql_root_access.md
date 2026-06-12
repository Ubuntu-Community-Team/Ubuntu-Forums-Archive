---
title: "resetting mysql root access"
date: 2006-08-14
forum: General Help
---

### Post by mwallis on 2006-08-14
Hi ...

I have 6.06 installed, have LAMP setup and I went to add a new database (to try some Ruby on Rails stuff) and I can't get access authority to set it up. When I run mysql as me I see

```
[mwallis@drake]:/home/mwallis 329 > mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 26 to server version: 5.0.22-Debian_0ubuntu6.06-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| EngLab             | 
+--------------------+
2 rows in set (0.00 sec)

mysql> 
```

When I try to login as user root, I get the infamous 

```

[mwallis@drake]:/home/mwallis 330 > mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
[mwallis@drake]:/home/mwallis 331 >

```

I tried doing [COLOR="Red"]sudo apt-get remove mysql-server; sudo apt-get install mysql-server[/COLOR] but I still get the same Access denied msg.

I see in /etc/mysql/debian.cnf that the system uses debian-sys-maint as a user but I don't seem to have a way to decode the password that's in the file.

---

### Post by mwallis on 2006-08-14
Ok ... found the workaround in the MySQL site (finally).

You need to stop the current mysql process. In my case, I ran 

<CODE>
sudo /etc/init.d/mysql stop
</CODE>

Then create a text file that is in a place accessable to the mysqld when it runs (I used /tmp/t1) and put the following text in the file (using your editor of choice):

<CODE>[COLOR="Red"]SET PASSWORD FOR 'root'@'localhost' = PASSWORD('[COLOR="Black"]YourNewPassword[/COLOR]');
[/COLOR]</CODE>

Save your file and then run the following command:

<CODE>sudo mysqld_safe --init-file=[COLOR="Red"]/tmp/t1[/COLOR] &
</CODE>

where you replace /tmp/t1 with the full path to the file you just edited.

This will start the server and run the command in the file, which resets your root password. You can now login to mysql as root using:

<CODE>mysql -p -u root
</CODE>

and supplying your new password at the prompt.

---

### Post by az on 2006-08-14
> **mwallis said:**
> 
When I try to login as user root, I get the infamous 

```

[mwallis@drake]:/home/mwallis 330 > mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
[mwallis@drake]:/home/mwallis 331 >

```


Even if you knew the password, you would have to run mysql with the -p switch to use it.  Mysql is obtuse like that.

mysql -u root -p

and then enter the password at the prompt.

---

### Post by jalak on 2006-09-18
I recently had this issue, this is how to fix it...

1. Stop Mysqld by /etc/init.d/mysql stop
2. Go into /var/lib/mysql
2. Rename the mysql folder to mysql- (or something similiar)
3. Run mysql_install_db

That should fix the problem..

---

### Post by hasimir44 on 2007-05-26
This may help someone.. How to set/change a password from inside mysql.. 


```
UPDATE mysql.user SET Password=PASSWORD('newpassword')
WHERE User='root';
FLUSH PRIVILEGES;
```

---

### Post by juano816 on 2007-06-05
To all users that foolishly deleted the root user from Mysql and have no access at all

note: the following steps will most likely remove any database created so only do this if you don't care about what you had created in mysql prior to the problem.

from terminal enter into unix root

command:
sudo su
or
su

now purge mysql server

command:
sudo aptitude --purge remove packagename

browse into  /var/lib/mysql this folder should be deleted. i did it this way

command:
rm -rf   /var/lib/mysql

that will wipe the folder. (that command is dangerous wrong spaces in your directory string will wipe out your universe. i dont know exactly what that means but it does not sound good. what i typed woks great

if you reinstall everything should be fresh

---

