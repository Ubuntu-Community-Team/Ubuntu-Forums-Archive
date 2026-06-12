---
title: "no problem!!!!!!"
date: 2013-01-14
forum: General Help
---

### Post by ankt90138 on 2013-01-14
hello i cant find bug in this line its not working!!!

13 * * * * /usr/sbin/rtcwake -m mem -s 60


i hava also added a newline at end of this ..:popcorn:

---

### Post by sudodus on 2013-01-14
Welcome to the Ubuntu Forums :-)

I haven't used that command myself but assume you need root privileges. Are you running it with your user's crontab or with root's crontab?

```
sudo crontab -e
```

---

### Post by SlugSlug on 2013-01-14
are you using roots cron or your own?

---

### Post by ankt90138 on 2013-01-14
sir im using user crontab

---

### Post by ankt90138 on 2013-01-14
im just using user's crontab....and that command 
i ran from terminal works fine...sleeps pc for 60 seconds

---

### Post by hydn79 on 2013-01-14
To edit crons you should use:
> sudo crontab -u root -e

---

### Post by SlugSlug on 2013-01-14
> **ankt90138 said:**
> im just using user's crontab....and that command 
i ran from terminal works fine...sleeps pc for 60 seconds
Does it not need sudo ?

---

### Post by ankt90138 on 2013-01-14
not thats working fine..only rooted cron jobs works in ubuntu precise..

how to start.stop and restart those jobs..
over the internet irs written /etc/init.d/crond start/stop/restart but this command is not working.no such file or directory...

plz tell how do i start or stop these jobs..

---

### Post by 3rdalbum on 2013-01-14
Sorry, double post.

---

### Post by 3rdalbum on 2013-01-14
> **ankt90138 said:**
> not thats working fine..only rooted cron jobs works in ubuntu precise..

how to start.stop and restart those jobs..
over the internet irs written /etc/init.d/crond start/stop/restart but this command is not working.no such file or directory...

plz tell how do i start or stop these jobs..

Your information is outdated. These days Ubuntu uses a different system to control services:

```
sudo service crond start
```

---

### Post by ankt90138 on 2013-01-15
it says unrecognised service

---

### Post by ankt90138 on 2013-01-16
unrecognised service

---

### Post by sudodus on 2013-01-16
I think cron is a standard service of most linux distibutions and versions. But to be sure we talk about the same thing, please let us know which version and flavour of Ubuntu you are running. For example

- version: 12.04, 10.04, 11.10, 12.10 (other versions have passed end of life, or are not yet released)

- flavour: [vanilla] Ubuntu, Kubuntu, Lubuntu, Xubuntu ...

You can find the version with the following command:
```
lsb_release -a
```

I am running 12.04, and when I run the following command
```
ps -A|grep cron
```
I get the following output
```
 1368 ?        00:00:00 cron
```
which means that there is a process [FONT="Courier New"][SIZE="3"]cron[/SIZE][/FONT] running (and it has the process ID pid=1368).

If it is running for you too, it should work, if you enter your command into root's crontab with

```
sudo crontab -e
```

If you change the line to
```
* * * * * /usr/sbin/rtcwake -m mem -s 15
```
the computer should be put to sleep for 15 seconds each minute instead of once every hour (at 13 minutes past each even hour).

You can also test that crontab is working by testing with some very simple command, for example writing a line to a file in a directory with write access

```
/bin/echo 'hello world'>/tmp/hello.txt
```

---

