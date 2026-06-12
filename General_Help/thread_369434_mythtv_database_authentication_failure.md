---
title: "mythtv database authentication failure"
date: 2007-02-24
forum: General Help
---

### Post by linedpaper on 2007-02-24
I am trying to get mythtv up using the mythtv ubuntu wiki, but I can't get the backend to start due to authentication failure.  I went through and reset all my passwords for the databases and what not, but still having this issue.  anybody know what to do?

```
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```

---

### Post by wjston on 2007-02-26
> **linedpaper said:**
> I am trying to get mythtv up using the mythtv ubuntu wiki, but I can't get the backend to start due to authentication failure.  I went through and reset all my passwords for the databases and what not, but still having this issue.  anybody know what to do?

```
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```

Did you check to see if your password in /etc/mythtv/mysql.txt matches the one you set for your MySQL database? I know there have been some users who have had to manually change this to get things to connect.

---

### Post by superm1 on 2007-02-26
> **linedpaper said:**
> I am trying to get mythtv up using the mythtv ubuntu wiki, but I can't get the backend to start due to authentication failure.  I went through and reset all my passwords for the databases and what not, but still having this issue.  anybody know what to do?

```
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```
This doesn't necessarily mean that the backend didn't start.  Have you checked to see if the process is running, or what /var/log/mythtv/mythbackend.log says?

---

### Post by linedpaper on 2007-02-28
the backend did not start, and the passwords were all set correctly.  what i had to do to fix this was manually login as the user mythtv and run myth-setup again.  apparently there was an error in that config.  now everything is all good.

---

