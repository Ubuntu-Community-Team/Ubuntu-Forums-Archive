---
title: "user name question"
date: 2006-07-17
forum: General Help
---

### Post by lex1 on 2006-07-17
I want to know if the user "news" has been created.

When i installed suck and inn2 (InterNetNews) package
does the user "news" exist?

i am in fluxbox not gnome just as a point of information

etc/suck has all news permissions
total 24
drwxrwxr-x 2 news news 4096 2006-06-30 17:16 .
drwxr-xr-x 90 root root 4096 2006-07-17 06:02 ..
-rw-rw-r-- 1 news news 1946 2004-10-27 13:37 get-news.conf
-rw-rw-r-- 1 news news 56 2004-10-27 13:37 suckkillfile
-rw-r--r-- 1 news news 122 2006-07-05 11:15 sucknewsrc
-rw-rw-r-- 1 news news 124 2004-10-27 13:37 sucknewsrc.old






and etc/news has all root permissions
total 296
drwxr-xr-x 3 root root 4096 2006-07-11 12:23 .
drwxr-xr-x 90 root root 4096 2006-07-17 06:02 ..
-rw-r--r-- 1 root root 155 2006-03-15 10:39 actsync.cfg
-rw-r--r-- 1 root root 382 2006-03-15 10:39 actsync.ign
-rw-r--r-- 1 root root 304 2006-03-15 10:39 buffindexed.conf
-rw-r--r-- 1 root root 87179 2006-07-11 14:20 control.ctl
-rw-r--r-- 1 root root 859 2006-03-15 10:39 cycbuff.conf
-rw-r--r-- 1 root root 495 2006-03-15 10:39 distrib.pats
-rw-r--r-- 1 root root 1424 2006-03-15 10:39 expire.ctl
drwxr-xr-x 2 root root 4096 2006-06-29 11:37 filter
-rw-r--r-- 1 root root 5353 2006-03-15 10:39 incoming.conf
-rw-r--r-- 1 root root 4831 2006-07-10 18:42 inn.conf
-rw-r--r-- 1 root root 3179 2006-03-15 10:39 innfeed.conf
-rw-r--r-- 1 root root 72395 2006-03-15 10:39 innreport.conf
-rw-r--r-- 1 root root 2120 2006-03-15 10:39 innwatch.ctl
-rw-r--r-- 1 root root 1158 2006-03-15 10:39 moderators
-rw-r--r-- 1 root root 185 2006-03-15 10:39 motd.news
-rw-r--r-- 1 root root 609 2006-03-15 10:39 news2mail.cf
-rw-r--r-- 1 root root 5007 2006-07-05 14:26 newsfeeds
-rw-r--r-- 1 root root 516 2006-03-15 10:39 nnrpd.track
-rw-r--r-- 1 root root 583 2006-03-15 10:39 nntpsend.ctl
-rw-r--r-- 1 root root 4939 2006-03-15 10:39 ovdb.conf
-rw-r--r-- 1 root root 340 2006-03-15 10:39 overview.fmt
-rw-r----- 1 root news 597 2006-03-15 10:39 passwd.nntp
-rw-r--r-- 1 root root 1784 2006-03-15 10:39 radius.conf
-rw-r--r-- 1 root root 4898 2006-07-11 09:20 readers.conf
-rw-r--r-- 1 root root 911 2006-03-15 10:39 send-uucp.cf
-rw-r--r-- 1 root root 1430 2006-03-15 10:39 storage.conf
-rw-r--r-- 1 root root 114 2006-03-15 10:39 subscriptions


here is the result from finger news


Here is result from finger what does it mean?
has a user been creaed?



Login: news Name: news
Directory: /var/spool/news Shell: /bin/sh
Never logged in.
New mail received Tue Jul 11 03:02 2006 (BST)
Unread since Tue Jul 11 03:02 2006 (BST)
No Plan.
Edit/Delete Message 

so how to login to news? what is the password

Should all my permissions in etc/news from root to news?




lx1

---

### Post by mogelhead on 2006-07-17
> I want to know if the user "news" has been created.

All the users are listed in the file /etc/passwd

On my Kubuntu Breezy Badger (5.10), I have the user "news". I have not installed suck nor inn2.

What exactly are you trying to do?

---

### Post by mogelhead on 2006-07-21
Please don't cross post. (Don't start identical threads in different sub forums). 

lex1: [confused about user names]("http://www.ubuntuforums.org/showthread.php?t=217388") [Absolute Beginner Talk]

---

