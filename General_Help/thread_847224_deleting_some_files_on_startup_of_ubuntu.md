---
title: "deleting some files on startup of ubuntu"
date: 2008-07-02
forum: General Help
---

### Post by jagdishrao on 2008-07-02
hi guys

we are running a ubuntu machine as our demo server for serving Ruby on rails applications
we are using mysql,nginx,mongrel for serving the sites.

the problem is if for any reason the power fails out and comes back
mysql and nginx get started fine but mongrel does not work due to
some pid(mongrel.8000.pid  mongrel.8001.pid  mongrel.8002.pid) files
existing in log folder.

we then manually delete the files and start the mongrel cluster server.

is there anyway we can check during reboot of ubuntu server for any existing pid
files in log folder and delete them and then start the mongrel cluster.

thanks
jags

---

### Post by Titan8990 on 2008-07-02
There is a solution to this problem. What you are trying to do is work around the problem instead of solve it. I had similar issues with our ROR server. This set up guide made things perfect: [http://ubuntuforums.org/showthread.php?t=674598](http://ubuntuforums.org/showthread.php?t=674598).

Of course you will need to replace Redmine with whatever ROR application you are using.

This setup will ensure the your ROR server is always up on bootup even before a user has logged in. It also uses apache2 for better performance of the server.

---

