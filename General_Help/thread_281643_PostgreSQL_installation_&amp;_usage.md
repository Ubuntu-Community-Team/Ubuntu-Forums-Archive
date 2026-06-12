---
title: "PostgreSQL installation &amp; usage"
date: 2006-10-21
forum: General Help
---

### Post by geomantic8 on 2006-10-21
Not sure if this is the right forum for this posting but here goes...

**Problem:** I can't get PostgreSQL to work properly using the packages in the Synaptic distribution (8.1). 

**Background:** I have followed [these]("http://hocuspok.us/journal/postgresql-on-ubuntu-linux-how-to-updated") very good instructions to install 8.1.4, just for practice, but made some rookie mistakes and wound up uninstalling it. To save time (and because 8.1 will satisfy my needs) I decided to use the Synaptic packages to install. However, I can't seem to figure out how to 'initdb' and start 'postmaster'. 

Any insights would be much appreciated. Thanks in advance!

---

### Post by LeeVee on 2006-10-23
I followed the same instructions and also had a problem.
It appeared to install OK, but then came up with the following problem when it tried to start up;
"could not create log file /var/log/postgresql-8.1-main.log"

When I looked there, the file was there, and it had full RW permissions. I eve tried deleting and re-creating the file, but to no avail.
Postgresql just will not start if it can't open that file. ](*,) 

Sorry geomantic - I don't have an answer to the Synaptics startup problem. I would perhaps have re-installed Postgresql from scratch. :(

---

### Post by geomantic8 on 2006-10-23
> **LeeVee said:**
> I followed the same instructions and also had a problem.
It appeared to install OK, but then came up with the following problem when it tried to start up;
"could not create log file /var/log/postgresql-8.1-main.log":(

Right, and 'initdb' is unrecognized, as is all the other commands associated w/ PostgreSQL. 

Since I had better luck w/ the instructions I linked to in my previous post, I am going to uninstall the Synaptic-installed lot and re-install using those instructions. 

Still, I'd be interested to hear if others are having similar issues w/ PostgreSQL on Ubuntu, and/or if there's something obvious I'm overlooking.

---

### Post by SolarBear on 2006-11-08
Have a look at this :
[http://www.postgresql.org/docs/8.1/interactive/tutorial-start.html]("http://www.postgresql.org/docs/8.1/interactive/tutorial-start.html")
and look at the bottom of the page. A user posted a very nice (and working, too !) way of getting Postgres to work using Ubuntu.

---

### Post by geomantic8 on 2006-11-27
Just a brief thanks. You're right, this is a very useful post. I'll retrace my steps as soon as I get the chance. 
-g8

---

### Post by pstep9407 on 2007-03-05
Thanks for the help, the link is nice. However, I get the following error when I get to the point of creating a database:

> Error: /etc/postgresql-common/user_clusters line 23: cluster */* does not exist

Any ideas?

---

