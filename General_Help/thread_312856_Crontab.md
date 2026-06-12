---
title: "Crontab"
date: 2006-12-05
forum: General Help
---

### Post by dannytherocker on 2006-12-05
Hi, I edited this (sudo crontab -e):

```
46 09 * * * apt-get -y update && apt-get -y upgrade && echo "upgrade ok: $(date)" >> /home/danilo/Desktop/mybackup.log

```

to get my (family) pc updated, but doesn't work! I noticed it because update-notifier today notified me about 4 updates, but the "orange cube" (update-notifier) did not disappear! So I decided to check it out by command top: crontab runs only "apt-get update" but does not run "apt-get -y upgrade && echo..........."
The same thing happen on my pc running Edgy (family runs dapper)...
What's wrong with my crontab?
thanks

---

### Post by reclusivemonkey on 2006-12-05
> **dannytherocker said:**
> Hi, I edited this (sudo crontab -e):

```
46 09 * * * apt-get -y update && apt-get -y upgrade && echo "upgrade ok: $(date)" >> /home/danilo/Desktop/mybackup.log

```

to get my (family) pc updated, but doesn't work! I noticed it because update-notifier today notified me about 4 updates, but the "orange cube" (update-notifier) did not disappear! So I decided to check it out by command top: crontab runs only "apt-get update" but does not run "apt-get -y upgrade && echo..........."
The same thing happen on my pc running Edgy (family runs dapper)...
What's wrong with my crontab?
thanks

apt-get isn't running as root.

---

### Post by dannytherocker on 2006-12-05
> **reclusivemonkey said:**
> apt-get isn't running as root.

yes it does, I typed ```
**sudo** crontab -e
```

---

### Post by reclusivemonkey on 2006-12-05
> **dannytherocker said:**
> yes it does, I typed ```
**sudo** crontab -e
```

That means you edited your crontab as root. Not the same thing.

I suggest if you want to do something like this, you either;

write the whole routine as a bash script, make it owned by root, and then run it from cron, or become root, and add it to root's cron tasks.

---

### Post by dannytherocker on 2006-12-05
> **reclusivemonkey said:**
> That means you **edited** crontab as root. Not the same thing.

I suggest if you want to do something like this, you either;

write the whole routine as a bash script, make it owned by root, and then run it from cron, or become root, and add it to root's cron tasks.

maybe you're right! I'll be trying right now!....let you know asap !

---

### Post by dannytherocker on 2006-12-05
> **reclusivemonkey said:**
> That means you edited your crontab as root. Not the same thing.

I suggest if you want to do something like this, you either;

write the whole routine as a bash script, make it owned by root, and then run it from cron, or become root, and add it to root's cron tasks.

No! does not work even if I am root! maybe should try to edit a bash script and make it own by root! :-(

---

### Post by reclusivemonkey on 2006-12-05
When I get home after work I will have a look at this see what I can do.

---

### Post by dannytherocker on 2006-12-05
> **reclusivemonkey said:**
> When I get home after work I will have a look at this see what I can do.

you are very very kind! but I fixed it all: just added this line to crontab 
```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
```
now everything is fine!!
Thank you very much for your help! :-)
Dan

---

### Post by reclusivemonkey on 2006-12-05
> **dannytherocker said:**
> you are very very kind! but I fixed it all: just added this line to crontab 
```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
```
now everything is fine!!
Thank you very much for your help! :-)
Dan

No problem. I clean forgot about that. When adding jobs to cron, its best to use the full path for a command. If you don't know this, use

```

which *command*

```

---

