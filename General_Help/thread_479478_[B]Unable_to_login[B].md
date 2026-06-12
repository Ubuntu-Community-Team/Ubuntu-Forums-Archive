---
title: "[B]Unable to login[/B]"
date: 2007-06-20
forum: General Help
---

### Post by ran_foru on 2007-06-20
Hi..

Whenever i try to login i get the message below and when i press ok i get logout automatic

[B]
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.


View details(~/.xsession-errors file)
[/B]

When I press ok to view message i get 


/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ranjan"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ranjan:/tmp/.ICE-unix/5302


Thx for any suggesition

---

### Post by dannyboy79 on 2007-06-20
is your /home directory full???

df -h
will show you amount of space used and remaining. This is the most common cause. Otherwise it's a permission issue, meaning the directory it's trying to write to, isn't writable for whatever reason. Could you ever login? is this just recently? If you didn't play with chmod then I am guessing you saved too much within your /home directory or whatver partition /home is mounted on.

---

### Post by shearn89 on 2007-06-20
try starting a session in safe-mode. May allow you to remove some files from the /home directory if you're full.
Or you could boot using a live disc, and remove some non-essential files from /home that way.

I had a similar problem when i ran out of room on the root partition, so if you can get to a terminal you could try removing some non-essential packages.

---

### Post by ran_foru on 2007-06-20
> **dannyboy79 said:**
> is your /home directory full???

df -h
will show you amount of space used and remaining. This is the most common cause. Otherwise it's a permission issue, meaning the directory it's trying to write to, isn't writable for whatever reason. Could you ever login? is this just recently? If you didn't play with chmod then I am guessing you saved too much within your /home directory or whatver partition /home is mounted on.


Hi 

I have enough space in home and other directory nearly 5gb and it might be permission problem

---

### Post by dannyboy79 on 2007-06-20
does your /tmp folders permissions and owner look like this?

drwxrwxrwt  14 root root  4096 2007-06-20 11:20 tmp

---

### Post by ran_foru on 2007-06-20
> **dannyboy79 said:**
> does your /tmp folders permissions and owner look like this?

drwxrwxrwt  14 root root  4096 2007-06-20 11:20 tmp


the permission of temp directory is 
drwxrwxrwt 17 root root 4096 2007-06-21 01:33 /tmp

---

### Post by dannyboy79 on 2007-06-20
here's a tip or 2. my suggestion would be to search the forums as this is not an uncommon problem.

[http://ubuntuforums.org/showthread.php?t=440792&highlight=Your+session+only+lasted+less+than+10+seconds](http://ubuntuforums.org/showthread.php?t=440792&highlight=Your+session+only+lasted+less+than+10+seconds)

---

### Post by bapoumba on 2007-06-20
Thread moved to "General Help".
Other threads you might want to check:
[http://ubuntuforums.org/showthread.php?t=447135]("http://ubuntuforums.org/showthread.php?t=447135")
[http://ubuntuforums.org/showthread.php?t=461241]("http://ubuntuforums.org/showthread.php?t=461241")

---

