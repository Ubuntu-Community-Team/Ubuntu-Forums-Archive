---
title: "users and groups -command line"
date: 2006-07-02
forum: General Help
---

### Post by lex1 on 2006-07-02
I have two users admin and lex1

in postfix i have the same but for some reason i cannot log in to admin
only lex1.

where are the list of uers and there permissions to be found?
if i do ps aux command admin is not listed no processes nothing

On the gnome desktop it's in	

System -> Administration -> Users and Groups

but i do not have a gnome desktop I am in Fluxbox.

so which directory and file do I look for from the command line?

lex1

---

### Post by blackjack6.21.91 on 2006-07-02
System -> Administration -> Users and Groups
if your in gn0me

peace dude

---

### Post by lex1 on 2006-07-02
Thanks for post.
and if i am useing fluxbox?

lex1

---

### Post by Fac51 on 2006-07-03
first, what's with the user "admin"
just use sudo or activate root 

to activate root:
```
user@host:~$ sudo passwd root
```

as for command line administration of users and groups

```
user@host:~$ man <usermod/useradd/userdel/users/groupmod/groupadd/groupdel/groups>   <---one at a time (of course)
```

i hope that helps, enjoy!

---

### Post by lex1 on 2006-07-03
cannot sign in as admin

no man pages for any of above suggestions in last post.

lex1

---

### Post by Ramses de Norre on 2006-07-03
Do you use the admin user for root tasks or just as a second user? What error do you get on loging in as admin?
And there are man pages for those commands ;) "man adduser" or any other works here.

---

### Post by Fac51 on 2006-07-03
please tell me that you did not include the "< >"'s

it's not hard buddy, you can do it, i have faith](*,)

---

### Post by lex1 on 2006-07-04
yes man pages do work but alas i do not understand them

forgooten or never have log in to admin.

reason for question i have been hacked!
18:53:43--i was out that afternoon and evening

-------------------------------------------------------------
Jun 28 18:07:49 xstation sshd[5446]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=86.80-203-198.nextgentel.com
Jun 28 18:07:50 xstation sshd[5446]: Failed password for invalid user shop from 80.203.198.86 port 57972 ssh2
Jun 28 18:17:01 xstation CRON[5448]: (pam_unix) session opened for user root by (uid=0)
Jun 28 18:17:01 xstation CRON[5448]: (pam_unix) session closed for user root
Jun 28 18:53:43 xstation sshd[5455]: Accepted password for admin from 85.186.211.151 port 1283 ssh2
Jun 28 18:53:43 xstation sshd[5457]: (pam_unix) session opened for user admin by (uid=0)
Jun 28 18:54:03 xstation sshd[5457]: (pam_unix) session closed for user admin
Jun 28 19:17:01 xstation CRON[5483]: (pam_unix) session opened for user root by (uid=0)
Jun 28 19:17:01 xstation CRON[5483]: (pam_unix) session closed for user root
Jun 28 20:17:01 xstation CRON[5489]: (pam_unix) session opened for user root by (uid=0)
Jun 28 20:17:01 xstation CRON[5489]: (pam_unix) session closed for user root
Jun 28 21:17:01 xstation CRON[5496]: (pam_unix) session opened for user root by (uid=0)
Jun 28 21:17:01 xstation CRON[5496]: (pam_unix) session closed for user root
Jun 28 22:17:01 xstation CRON[5503]: (pam_unix) session opened for user root by (uid=0)
Jun 28 22:17:01 xstation CRON[5503]: (pam_unix) session closed for user root
Jun 28 22:48:30 xstation gdm[3816]: (pam_unix) session closed for user lex1

Jun 28 22:48:54 xstation sshd[3947]: Received signal 15; terminating.






-----------------------------------------------------------------

ps aux reveles that admin does not use any PID;s
OR processess.

admin as far as i understand is just in postfix as an address to my domain.

lex1

---

### Post by Ramses de Norre on 2006-07-04
> **lex1]here is thread

[http://www.ubuntuforums.org/showthread.php?t=208775](http://www.ubuntuforums.org/showthread.php?t=208775)

yes man pages do work but alas i do not understand them

forgooten or never have log in to admin. 

reason for question i have been hacked!
18:53:43--i was out that afternoon and evening
-------------------------------------------------------------
Jun 28 18:07:49 xstation sshd[5446]: (pam_unix) authentication failure said:**
> : Failed password for invalid user shop from 80.203.198.86 port 57972 ssh2
Jun 28 18:17:01 xstation CRON[5448]: (pam_unix) session opened for user root by (uid=0)
Jun 28 18:17:01 xstation CRON[5448]: (pam_unix) session closed for user root
Jun 28 18:53:43 xstation sshd[5455]: Accepted password for admin from 85.186.211.151 port 1283 ssh2
Jun 28 18:53:43 xstation sshd[5457]: (pam_unix) session opened for user admin by (uid=0)
Jun 28 18:54:03 xstation sshd[5457]: (pam_unix) session closed for user admin
Jun 28 19:17:01 xstation CRON[5483]: (pam_unix) session opened for user root by (uid=0)
Jun 28 19:17:01 xstation CRON[5483]: (pam_unix) session closed for user root
Jun 28 20:17:01 xstation CRON[5489]: (pam_unix) session opened for user root by (uid=0)
Jun 28 20:17:01 xstation CRON[5489]: (pam_unix) session closed for user root
Jun 28 21:17:01 xstation CRON[5496]: (pam_unix) session opened for user root by (uid=0)
Jun 28 21:17:01 xstation CRON[5496]: (pam_unix) session closed for user root
Jun 28 22:17:01 xstation CRON[5503]: (pam_unix) session opened for user root by (uid=0)
Jun 28 22:17:01 xstation CRON[5503]: (pam_unix) session closed for user root
Jun 28 22:48:30 xstation gdm[3816]: (pam_unix) session closed for user lex1

Jun 28 22:48:54 xstation sshd[3947]: Received signal 15; terminating.
-----------------------------------------------------------------
ps aux reveles that admin does not use any PID;s 
OR processess.

Hmm do you need the admin user? How did you create it? Why can't you log in to admin? 
I'd say change your password for the hacking and see if you're able to track down the ip of the hacker and blacklist it. I'd also deny sudo priviliges on all user accept of one, as you see the hacker was able to log into root from the admin user.

In fact I don't really see what you've done/are trying to do. A little more details could be helpful.

---

### Post by lex1 on 2006-07-04
thanks for post.

I an trying to log into admin cannot rememer password.

what is command line for access to admin NOT have gui like in gnome.

How do i blacklist ip FROM romainia?

yes i do need admin account for email.

what more can  i give to help


lex1

---

### Post by Ramses de Norre on 2006-07-04
You don't remember the passwd for admin? Do "sudo passwd admin" as user lex1 and you'll be able to set a new one.
For login into other user from terminal do su 'username' or go in a tty (ctrl+alt+F1-6) and log in there.
I don't really know how to blacklist the ip but I'm pretty sure it's possible.

---

### Post by lex1 on 2006-07-04
thanks for your advice on this topic :D :D 

login to admin ok now

lex1**

---

### Post by Rui Pais on 2006-07-04
hi,
hi think to blacklist ips you need to add it to /etc/hosts.deny

You should narrow down root access to only one user. And if you have your box exposed to net i wouldn't put root account with a password. Thats asking for trouble... it's not exactly a secret that root is the adminstrative user for lot of *nixs, so hackers will esally try that account and only need to find the password not username+password. 
If you need to have an user (named admin or other) with root access to some commands you can add those to sudo list using:
```
sudo visudo
```
and add one by one. The syntax is explained with examples on the file and man visudo.

---

### Post by lex1 on 2006-07-04
ok thanks for your post.

managed to sort out the hosts.deny file.

although the visudo is a little beyond me even with the man file.

lex1

---

### Post by Rui Pais on 2006-07-04
well, i don't know what you do as admin user, but for security you should set only one user with administrative powers.

An abstract example. 
Imagine that you want user admin to run some script like /usr/local/bin/backupoldmails.
Instead of put admin on the wheel group (that would give access to root powers), just visudo and add the line:
> admin ALL=(ALL) /usr/local/bin/backupoldmails

now if admin type:
```
sudo cat /etc/shadow
```
(or any other root required task) sudo will deny it and will report the incident to root.
But if admin runs
```
sudo /usr/local/bin/backupoldmails 
```
it just need to give password.

---

### Post by lex1 on 2006-07-04
thanks for post.

admin is just used for mail.

lex1 is the main user.

lex1

---

