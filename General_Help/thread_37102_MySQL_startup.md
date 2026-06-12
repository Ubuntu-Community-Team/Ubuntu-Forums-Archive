---
title: "MySQL startup"
date: 2005-05-25
forum: General Help
---

### Post by nyrmlieber on 2005-05-25
I did something terrible! I changed my.cnf so I could access the server from other computers on the network. Then, I assumed I needed to restart mysql. Instead of doing to right thing and using the command: /etc/init.d/mysql restart, I shutdown the server iside of the mySQL console manager. Now I cant get the server to start! I says it can't connect through the socket: /var/run/mysqld/mysql.sock. I looked for that file, and it isn't even there! How do I get it back?

---

### Post by judabuddhist on 2005-05-26
I've been trying to get mysql to work in the first place, and have come across the same error. I have no clue why.

---

### Post by malaprohibita on 2005-05-29
There's a lot of documentation on the problem, just Google it.  One caveat, though:  there are apparently a number of potential causes, and I never could get MySQL to work under Mandrake 10.1,  I could, ironically, under Ubuntu.

Good luck!

---

### Post by Oline61 on 2005-05-29
You might try removing MySQL (sudo apt-get remove mysql) and the reinstalling the package. You probably should reinstall the control center too just to be on the safe side.

I have MySQL running and haven't had any problems so far.

---

### Post by Mez on 2005-05-29
[QUOTE=Oline61]You might try removing MySQL (sudo apt-get remove mysql) and the reinstalling the package. You probably should reinstall the control center too just to be on the safe side.

I have MySQL running and haven't had any problems so far.[/QUOTE]
 try this

```
sudo slocate -u
sudo slocate mysql.sock
```

If this finds a file, then your config is just pointting to the wrong place, and you need to symlink it to the new place

```
sudo ln -s /bla/bla/bla/mysql.sock /var/run/mysqld/mysql.sock
```

replace /bla/bla/bla/mysql.sock with whatever it finds in the above slocate commands

---

### Post by ensenadaubuntulover on 2005-05-29
[QUOTE=Oline61]You might try removing MySQL (sudo apt-get remove mysql) and the reinstalling the package. You probably should reinstall the control center too just to be on the safe side.

I have MySQL running and haven't had any problems so far.[/QUOTE]
 I installed Mysql it seems to work, if I use webmin I can create databases and tables but I instaled phpmyadmin (a sugestion from a tutorial) but ask for password but doesent seem to recignize my password because ubuntu has only sudo and no root so I am at a loss

I get to enter but no privileges for making databases

---

### Post by ensenadaubuntulover on 2005-05-29
:)

---

### Post by MadCowDzz on 2006-01-06
[QUOTE=Mez]try this

```
sudo slocate -u
sudo slocate mysql.sock
```

If this finds a file, then your config is just pointting to the wrong place, and you need to symlink it to the new place

```
sudo ln -s /bla/bla/bla/mysql.sock /var/run/mysqld/mysql.sock
```

replace /bla/bla/bla/mysql.sock with whatever it finds in the above slocate commands[/QUOTE]

Sorry to bump an old thread... What happens if the above command doesn't find a file?

A script that ran fine on my old installation (Suse 10) doesn't want to work on my new Ubuntu box... *Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)*

I've checked all the normal locations of mysql.sock, but can't find it.

Alternatively, if I remove MySQL (with apt-get), will I lose the databases I've already set up?

---

### Post by adamkane on 2006-04-01
I've found that you have to install apache/mysql/php correctly the first time, and hope nothing gets broken. I have yet to find out how to re-install mysql4 on Ubuntu or how to back up an apache2/mysql4/php5 installation.

There are too many things that can go wrong. Tracking down errors requires days of effort. Ubuntu re-install is usually the only option.

---

### Post by GiantsFanMan11 on 2006-04-24
[QUOTE=MadCowDzz]Sorry to bump an old thread... What happens if the above command doesn't find a file?

A script that ran fine on my old installation (Suse 10) doesn't want to work on my new Ubuntu box... *Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)*

I've checked all the normal locations of mysql.sock, but can't find it.

Alternatively, if I remove MySQL (with apt-get), will I lose the databases I've already set up?[/QUOTE]

Try searching for "mysqld.sock" because that is the file that runs MySQL for me.
-Steve

---

### Post by cromestant on 2006-05-19
By the way, Ubuntu Does have a root user, you just have not set it up yet

just do
sudo passwd root

then enter the user password, ( for sudo) then enter the new root password.

also, try checking this out ( as root)
/etc/init.d/mysql start ( or restart)

then do a ps and see if the mysqld daemon is running

---

