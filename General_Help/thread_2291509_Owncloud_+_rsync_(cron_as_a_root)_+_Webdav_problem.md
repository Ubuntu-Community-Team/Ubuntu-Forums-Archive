---
title: "Owncloud + rsync (cron as a root) + Webdav problem"
date: 2015-08-20
forum: General Help
---

### Post by pasi.hakkarainen on 2015-08-20
Hi!

I have a problem and I am trying to tell you what it is and how am I tried to solve it (without luck). I hope I'll get good feedback and hopefully ideas how to do this (if and probably when there is a better way).

So... I have owncloud server running in my Ubuntu 14.04 server. Purpose of that owncloud is get automaticly all photos & videos from mine & wife phones. Everything works for that really nice. All photos & videos are stored in /var/www/owncloud/data/"username" folder and its subdirectories.

This has been done with instructions found here: [https://www.howtoforge.com/how-to-install-owncloud-7-on-ubuntu-14.04](https://www.howtoforge.com/how-to-install-owncloud-7-on-ubuntu-14.04)

What I want is backup & copy all photos to the different hdd:s which are also samba-shared for handling those pics (wife has Win7). I want that this happened automatically and currently I am using rsync (cron job) for that. I have mounted WebDAV share and now on my username this works like a charm & my rsync cron job is working.

However I do not know how to run rsync cron job as a root because otherwise there is a problem for read that wife owncloud data from owncloud directory.

So I tried to do this same to my wife account but it needs my manual login with her username&password that this mounts happening.

My questions:


[LIST]
[*]is this really stupid way to do this - and if yes what would be better way
[*]How can I run rsync cron job as a root? (Then I do not need webdav mount to my wife)
[*]Or how can I mount automatically can mount also my wife account when ubuntu starts?
[/LIST]

I hope you understood my question... If not - just ask then I am trying to clarify. And yes I am not a linux/ubuntu specialist!

---

### Post by apmcd47 on 2015-08-20
I don't think I can answer all your questions, but to edit the root crontab use```
sudo crontab -e
```to create a root crontab, or (I only discovered this recently)```
sudoedit /etc/crontab
```Be aware that the format of these two are different - the latter requires the name of the user the command is to be executed as.

Andrew

---

