---
title: "I need help with the root admin"
date: 2007-08-22
forum: General Help
---

### Post by itsryan on 2007-08-22
I need to log in to the root admin to run a command so i can start a server. 
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) thats the server i need to install.
This is the command i need to run 
# Go to a Linux shell and login as the system administrator root:

su

# Extract the downloaded archive file to /opt:

tar xvfz xampp-linux-1.6.3b.tar.gz -C /opt

I am very new to ubuntu and i need some help.

---

### Post by itsryan on 2007-08-23
I realy just need to know how to extract the files in to the opt folder.

---

### Post by jamvegan on 2007-08-23
The way that Ubuntu is set up by default, there is no root login.  Instead, the user that you create during the install process has all the privileges of "root", via a mechanism called "sudo".  Whenever you are trying to run a command in a terminal which requires root admin privileges, simply add sudo to the beginning of it.  Thus:
```
sudo tar xvfz xampp-linux-1.6.3b.tar.gz -C /opt
```
You will be asked for your password (your normal password, the one that you use to log in with), and then the command will be run with root privileges.  Incidentally, do not worry if you run several sudo commands and the shell does not always prompt you for you password.  For a few minutes after checking your password it assumes that you're still you and doesn't bother to ask you for your password again.

Note that if you are following instructions that tell you to su to root and then run a bunch of commands, you may need to preface each of the commands with "sudo" (certainly any that create or alter system files).

---

### Post by itsryan on 2007-08-23
ok well how to i get the files extracted to the opt file. It says i dont have the right privlages.

---

### Post by louieb on 2007-08-23
I  have used xampp and it pretty good. However just got a new PC to run Linux on and found another way to get lamp running.  If you haven't already installed xampp look here: [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP") What it boils down to to get LAMP up and running use:

```
sudo tasksel install lamp-server
``` 

Just follow the guide there is some setup stuff for apache and mysql  and put you website in /var/www/ and your all set.

If your not going to use Dyndns then you can change the permissions  so you can edit the website at will```
 sudo chmod 777 /var/www 
```

---

### Post by jamvegan on 2007-08-23
> **itsryan said:**
> ok well how to i get the files extracted to the opt file. It says i dont have the right privlages.

It looks like louieb's suggestion might be an easier way to go, but you're still going to have to use sudo.  Are you logged in as the first user that was created when Ubuntu was installed?  If so, sudo and your password should give you privileges to write to /opt, or anywhere else.  If not--if someone else is the system administrator--then you either need to get them to give you admin privileges, or do the install for you.

---

