---
title: "MySQL help: can't connect through socket /var/run/mysql/mysqld.sock"
date: 2007-09-15
forum: General Help
---

### Post by nala on 2007-09-15
Hi everyone. I have a fresh MySQL install on my (non server) Ubuntu Feisty box. I would like to log in and start getting some work done, but no such luck. I was following the directions on UbuntuGuide, but I am not able to log in as root and change the password. Whenever I try, I get this:

me@computer:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

There is in fact a file in that directory names mysqld.sock, so I don't know what the problem is. I'm getting really frustrated! Any help would be greatly appreciated. Please give verbose help, as I'm still not great with command line stuff and I know next to nothing about databases.

random background info:
I'm doing stuff for work on my own personal machine, so I am not interested in setting up a server. I also would rather not take connections from other machines.

---

### Post by Irihapeti on 2007-09-15
Nala:
I'm in a very similar situation. Just started playing with MySQL for very similar reasons to yours. What I found very helpful was the following link.

[http://www.webdevelopersnotes.com/tutorials/sql/installing_mysql_on_linux.php3](http://www.webdevelopersnotes.com/tutorials/sql/installing_mysql_on_linux.php3)

It's an online tutorial, written for utter beginners like us. 

HTH
Irihapeti

---

### Post by nala on 2007-09-15
Thanks for the link. I still seem to be stuck. I uninstalled and reinstalled mysql, but I'm getting access denied errors. 

mysqladmin: connect to server at 'localhost' failed

Gah. X.X;;;

---

### Post by kebes on 2007-09-15
> **nala said:**
> 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


Such errors can arise for a variety of reasons. Here are some things to try:

1. See if you can access it explicitly via "127.0.0.1" (which is just the IP address of "this computer"):
```

mysql -u root -p -h 127.0.0.1

```
If that works, then you can just explicitly use that address to connect. (See also #2 about possibly fixing this.)

2. When you run mysql without a specified host (switch "-h") then it tries to use "localhost"... however your definition of "localhost" might be wrong. In the file "/etc/hosts" you should have a line that says something like "127.0.0.1 localhost". So edit that file:
```

cd /etc/
sudo nano hosts

```
Make sure there is a line like:
```

127.0.0.1       localhost

```
If there isn't a line like that, then add it (or modify it) and save the file.

3. You can manually set your hostname to "localhost" this might fix it. So edit the file "/etc/hostname" and make sure it is set to "localhost". (You might not want to do this if you've given your computer a hostname that other things rely upon.)

4. Check the file "/etc/mysql/my.cnf" and find the value for "bind-address". In a normal situation, it should be set to "127.0.0.1". To do this:
```

cd /etc/mysql/
sudo nano my.cnf

```
Scroll down to the line that says "bind-address". It should look like this:
```
bind-address            = 127.0.0.1
```

5. Make sure permissions on the file "/var/run/mysqld/mysqld.sock" are proper:
```

cd /var/run/
ls -laF

```
Should return (among other things):
```

drwxr-xr-x  2 mysql      root         80 2007-07-14 16:06 mysqld/

```
Note the part that says "drwxr-xr-x" and that the owner is "mysql". This is important! If those are wrong, fix them with "chmod" and "chown" respectively:
```

sudo chown mysql:root mysqld
sudo chmod 755 mysqld

```
Similarly for the contents of that directory:
```

cd /var/run/mysqld/
ls -laF

```
Should give:
```
total 4
drwxr-xr-x  2 mysql root   80 2007-07-14 16:06 ./
drwxr-xr-x 19 root  root  760 2007-09-09 07:51 ../
-rw-rw----  1 mysql mysql   5 2007-07-14 16:06 mysqld.pid
srwxrwxrwx  1 mysql mysql   0 2007-07-14 16:06 mysqld.sock=

```
If not, fix it:
```
chown mysql:mysql *
sudo chmod 777 mysqld.sock
sudo chmod 660 mysqld.pid

```

6. Check if there is a "mysqld.sock" file in the directory "/tmp/":
```

cd /tmp/
ls *.sock

```
If so, you can change your settings to use that .sock file instead.



For any of these attempted fixes, you should restart MySQL before checking if they worked or not:
```
sudo /etc/init.d/mysql restart
```


I hope that helps.

---

