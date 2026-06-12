---
title: "Running a cron job with sudo privaleges"
date: 2007-05-22
forum: General Help
---

### Post by jethro10 on 2007-05-22
Hi,
1. if i run :-
myprog from a terminal I get errors,
2. if i run :-
sudo myprog its fine.

3. if I add the job :-
myprog to cron and pipe error messages to a file, I get the same errors as 1. above.

how do I add a job like 
sudo myprog
to cron ? as I wont be there to answer a password, and its running in the background anyhow!

am I missing something here ?
Ta
Jeff

---

### Post by akudewan on 2007-05-22
I'm not an expert on  this, but I think there are two kinds of Cron jobs: for users and for root. The root crontab is /etc/crontab.

If the task is put in /etc/crontab, then I think it will run as root.

---

### Post by Bachstelze on 2007-05-22
Just add it to root's crontab instead of yours.

```
sudo -i
crontab -e
```

---

### Post by jethro10 on 2007-05-24
> **HymnToLife said:**
> Just add it to root's crontab instead of yours.

```
sudo -i
crontab -e
```

Yep, thats it. works for me.

J

---

### Post by alzaf on 2007-07-14
Another thing you might find useful is that instead of cron sending the output to roots mail, you can get it  sent it to your own (mailx through CLI). It is done by the following command.

<CMD> -c | mail -s "subject header" <USERID>

Where <CMD> is the command you are running in cron and <USERID> is your user name that you log on with.

---

### Post by jelevin on 2007-09-22
This seems like a basic question, but try as I might, I really don't understand the difference between adding a job to /etc/crontab, putting it in the cron.d directory, and sudo crontab -e.  Are these all equivalent?

---

### Post by zurn on 2007-09-27
> **HymnToLife said:**
> Just add it to root's crontab instead of yours.

```
sudo -i
crontab -e
```

Thanks for the help, worked like a charm!

---

### Post by markdjones82 on 2007-12-22
what exactly does the -i option do anyway?

---

### Post by wally83 on 2008-01-20
> **jelevin said:**
> This seems like a basic question, but try as I might, I really don't understand the difference between adding a job to /etc/crontab, putting it in the cron.d directory, and sudo crontab -e.  Are these all equivalent?

IFAIK, you should not edit /etc/crontab manually, so just use crontab -e. 

Timing your own tasks:
```
crontab -e
```

Timing system wide / sudo-tasks:
```
sudo crontab -e
```

You don't need anything else.

> 
what exactly does the -i option do anyway?


It seems to be equivalent to 'sudo su', so it changes user to root. But actually you don't need to do that. You can also do that 'ubuntu way' aka 'sudo way':
sudo crontab -e

If you use that sudo -i or sudo su you have to type:
sudo -i
crontab -e
su <your username>   <- to switch back from user 'root'.

---

### Post by heindsight on 2008-01-20
> **wally83 said:**
> 
If you use that sudo -i or sudo su you have to type:
sudo -i
crontab -e
su <your username>   <- to switch back from user 'root'.

Actually, the correct way to end a root session started with sudo -i (or sudo -s or sudo su) is to use exit. 
Each of these commands starts a new shell with root privileges, once you're done working as root,
you need to exit from that root shell, which will bring you back to the shell from which you called sudo [-i|-s|su].

BTW. As far as I know, sudo -s and sudo su do the same thing, which is to just start a new shell as root, while sudo -i starts a login shell as root.

---

