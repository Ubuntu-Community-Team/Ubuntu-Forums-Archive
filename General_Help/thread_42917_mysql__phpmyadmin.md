---
title: "mysql / phpmyadmin"
date: 2005-06-19
forum: General Help
---

### Post by edacsac on 2005-06-19
Hi all, 

Love Ubuntu so far. Installation of packages via apt-get is totally awesome!

Question about mysql and phpmyadmin. where do I set up user(s) for mysql so I can login to phpmyadmin and get rolling? I've read that I can type mysql at the command line, and use the grant commands and what not, but under what directory do do this? I am the master of command not found today.  I've been searching every directory on my file system, and after hours of nothing I'm completely mentally exhuasted. Nothing like searching for hours on end, only to be no further than where you started.

Please help  :|

---

### Post by GrumpySimon on 2005-06-20
Have you installed MySQL via apt-get?

You can connect to mysql in a terminal like this:
```

mysql -u <username> -p

```

where <username> is something like 'root' or anything else you've enabled.

--Simon

---

### Post by afonic on 2005-06-20
The easiest way would be to use phpmyadmin.

In your first login, use username root and leave the password blank (as it is blank, because root password has not been set yet). Then get in users page and set passwords for both root users (localhost and localdomain). Then it will log you out and you need to login again with your new password. Now you can add /remove users. Note that I suggest removing the two "Any" users with read access for security reasons.

/Edit
I suggest you install both mysql-server and client as well as phpmyadmin using apt-get.

---

### Post by GrumpySimon on 2005-06-20
[QUOTE=afonic]The easiest way would be to use phpmyadmin.

In your first login, use username root and leave the password blank (as it is blank, because root password has not been set yet). Then get in users page and set passwords for both root users (localhost and localdomain). Then it will log you out and you need to login again with your new password. Now you can add /remove users. Note that I suggest removing the two "Any" users with read access for security reasons.

/Edit
I suggest you install both mysql-server and client as well as phpmyadmin using apt-get.[/QUOTE]
 While you're at it, get rid of anyone who can connect from '%' (ie: anywhere). I'm not sure what the default Ubuntu settings are, but the standard MySQL install ships with a number of them which is just asking for trouble.

--Simon

---

### Post by afonic on 2005-06-20
Actually they have two users that can connect read from everywhere which NEED to be removed for security reasons even if they are read-only (the "Any" ones for I said about).

Also they have two root accounts (@localhost and @localdomain), so it would be safe to remove the localdomain one. Finally there is a "debian-sys-maint" user with all privileges as well which is probably used for automated updates and stuff (and has a password by default). I am not sure is it's unsecure but it would be a good idea to remove all privileges from him and give them back only when you are about to upgrade MySQL via apt-get.

---

### Post by Seer on 2005-06-21
You know I made a discovery that has lead me to never install mysql/php/apache/myphp/etc ever again???

Because you can have a portable version of the lot along with the Mambo CMS using their brilliant Standalone Server tool.

[http://mamboforge.net/frs/download.php/5434/msas-web-installer.exe](http://mamboforge.net/frs/download.php/5434/msas-web-installer.exe)

You can extract it onto you USB memory stick and carry a fully featured web server around with you whereevr you go.

Just a suggestion - especially if you tend to have long term dev projects that need to be taken to clients or if you reinstall a lot like me :)

---

