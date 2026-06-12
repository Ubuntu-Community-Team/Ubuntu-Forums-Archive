---
title: "ssh session remain in list"
date: 2020-02-11
forum: General Help
---

### Post by amosss on 2020-02-11
Hi

Ubuntu 18.04.4


  I have a root user (login disabled) and a domain user. I ssh login with the domain user, disconnect and then reconnect.


  When I run loginctl list-sessions I see both sessions in the list, when I run w I only see my current session in the list.


  It seems that the previous session is never closed completely and remain as shadow forever. 
I added ClientAliveInterval=10m and ClientAliveCountMax=0 to sshd_config but it doesn't seem to have any effect.


  I use virtualmin that connects and disconnects the user every 5  minutes for his own stuff so that list grows quickly with those shadow  sessions.


  Is there something else I can do? 
Thanks

---

### Post by amosss on 2020-02-11
Here is the output of loginctrl list-sessions (after terminating everything and after some time)
SESSION        UID USER             SEAT             TTY
     c1173       1000 domain                          ???
     c1175       1000 domain                          ???
     c1171       1000 domain                          ???
     c1172       1000 domain                          ???
   2813719       1000 domain
     c1169       1000 domain                          ???
     c1174       1000 domain                          ???
     c1176       1000 domain                          ???
   2813721       1000 domain
     c1170       1000 domain                          ???

The lines with empty tty are ssh logins (719 is my previous one, 721 is the current one)
The others are of virtualmin.
None are closing by themselves.

---

### Post by amosss on 2020-02-12
Any kind of help will be appreciated, I wonder what's so special with my setup that this happens and it seems no many people encountered it.

---

### Post by deadflowr on 2020-02-12
How are you exiting the connections?

---

### Post by amosss on 2020-02-12
I exit with exit
How the sessions that virtualmin is creating exits, I have no idea.

---

### Post by amosss on 2020-02-13
After a boot I see this:

Feb 13 06:39:48 domain systemd[1]: Starting User Manager for UID 1000...
Feb 13 06:39:48 domain systemd[636]: Failed to create /user.slice/user-1000.slice/user@1000.service/init.scope control group: Permission denied
Feb 13 06:39:48 domain systemd[636]: Failed to allocate manager object: Permission denied
Feb 13 06:39:48 domain systemd[1]: [email]user@1000.servic[/email]e: Failed with result 'protocol'.
Feb 13 06:39:48 domain systemd[1]: Failed to start User Manager for UID 1000

Can it be related?

---

### Post by TheFu on 2020-02-13
The old-school commands, **who** and **last** tell the truth about current and old logins for any users, including LDAP users.
```
$ last|grep still
$ who
```
 
Use those until the systemd team breaks them.

---

### Post by amosss on 2020-02-13
w/who shows only one/current session
last|grep still shows
domain pts/0        IP    Thu Feb 13 22:15   still logged in  <<< I'm - current version I guess
reboot   system boot  4.15.0           Thu Feb 13 06:39   still running <<< this looks weird I must say but from reading in the internet it seems normal.

all w/who/etc... commands seem as if only one domain session is running (makes sense, I'm logged in using domain user via ssh) but loginctl list-sessions still accumulating... so someone is "lying" :)

last|grep domain
domain pts/0        IP    Thu Feb 13 22:15   still logged in
domain pts/0        IP    Thu Feb 13 22:13 - 22:14  (00:01)
domain pts/0        IP    Thu Feb 13 22:13 - 22:13  (00:00)
domain pts/0        IP    Thu Feb 13 22:08 - 22:12  (00:04)
domain pts/0        IP    Thu Feb 13 12:53 - 12:56  (00:02)
domain pts/0        IP    Thu Feb 13 07:24 - 07:37  (00:12)
domain pts/0        IP    Thu Feb 13 06:39 - 06:54  (00:14)
domain pts/0        IP    Thu Feb 13 06:36 - 06:38  (00:01)
domain pts/0        IP    Wed Feb 12 21:39 - 22:06  (00:26)
domain pts/0        IP    Wed Feb 12 20:41 - 21:19  (00:37)
domain pts/0        IP    Wed Feb 12 07:18 - 07:26  (00:07)
domain pts/0        IP    Tue Feb 11 19:35 - 19:36  (00:00)
domain pts/0        IP    Tue Feb 11 18:00 - 18:39  (00:38)
domain pts/0        IP    Tue Feb 11 18:00 - 18:00  (00:00)
domain pts/0        IP    Tue Feb 11 17:53 - 18:00  (00:06)
domain pts/0        IP    Tue Feb 11 07:33 - 07:38  (00:04)
domain pts/0        IP    Tue Feb 11 07:28 - 07:33  (00:05)
domain pts/0        IP    Tue Feb 11 06:59 - 07:27  (00:27)
domain pts/0        IP    Mon Feb 10 18:27 - 22:34  (04:07)
domain pts/1        IP    Mon Feb 10 18:09 - 18:27  (00:18)
domain pts/1        IP    Mon Feb 10 17:58 - 18:09  (00:10)
domain pts/1        IP    Mon Feb 10 17:24 - 17:56  (00:31)
domain pts/0        IP    Sun Feb  9 19:22 - 21:15  (01:52)
domain pts/0        IP    Fri Feb  7 19:14 - 19:24  (00:09)
domain pts/1        IP    Fri Feb  7 18:42 - 18:55  (00:12)
domain pts/0        IP    Fri Feb  7 18:21 - 18:48  (00:27)
domain pts/0        IP    Fri Feb  7 18:11 - 18:16  (00:04)
domain pts/0        IP    Fri Feb  7 13:44 - 14:36  (00:52)
domain pts/0        IP    Fri Feb  7 13:40 - 13:40  (00:00)
domain pts/0        IP    Fri Feb  7 13:31 - 13:39  (00:07)

It looks like the above are my ssh sessions (a guess), the appearance of the above just states the length of the sessions or that the sessions are still "out there"?

---

### Post by TheFu on 2020-02-13
**who** is showing multiple sessions here.
```
$ who
tf       pts/1        2020-02-13 09:35 (172.22.22.13)
tf       pts/3        2020-01-12 12:56 (:0.0)
tf       pts/4        2020-02-01 13:59 (172.22.22.11)
```
If I ssh in again, 
```
$ who
tf       pts/1        2020-02-13 09:35 (172.22.22.13)
**tf       pts/2        2020-02-13 18:52 (172.22.22.13)**
tf       pts/3        2020-01-12 12:56 (:0.0)
tf       pts/4        2020-02-01 13:59 (172.22.22.11)

```
Working as expected.

---

### Post by amosss on 2020-02-14
maybe w/who only shows alive sessions, like the (only) one I have and not the others which are ghosts.
what do you see when you run **loginctl list-sessions**?

---

### Post by TheFu on 2020-02-14
> **amosss said:**
> maybe w/who only shows alive sessions, like the (only) one I have and not the others which are ghosts.
what do you see when you run **loginctl list-sessions**?

Why do you care about loginctl at all?  Use the tools that are known to work correctly.  Good luck.

---

### Post by amosss on 2020-02-14
You mean loginctl is known as problematic, buggy and shouldn't be used at all?
Ignoring a problem won't make it go away...

---

