---
title: "How to install MySQL?"
date: 2020-04-06
forum: General Help
---

### Post by dchurch24 on 2020-04-06
Hi all,

This is something that has, to me at least, become more troublesome as the years have moved on. It was always a PITA to get MySQL installed, but over the last few years it feels like it's simply not possible any more.

I've installed it the usual way (apt-get install mysql-server), but these days it no longer asks you to set up a root password or new user etc... so I ran, mysql_secure_installation, and set the password up and took away anon access etc...

I then close that down and restart mysql as usual (service mysql start), and it starts up with no issue.

I then try to log in with the password I just set, and sure enough: Access denied for user 'root'@'localhost', so I went through in safe mode to set the password using "update mysql.user...blah..." and all is good. No errors.
I try to log in again using the password I just reset, and I get the same access deni

I've uninstalled mysql, and purged every mention of it, then reinstalled it, only to arrive at the exact same place.

I've been following the install instructions here: [https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04)

Any assistance would be truly appreciated. I'm sure I never had this trouble in the past, and have had successful websites up and running that I've written all using mysql. I used to be able to do a whole LAMP install in around 15-20 minutes.

---

### Post by spjackson on 2020-04-07
I'm assuming this is Ubuntu Studio 19.10 and not 9.10. The following works for me.
1. Get credentials from /etc/mysql//debian.conf
2. Start mysql using those credentials.
3. Then
```

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'New password goes here';

```

---

