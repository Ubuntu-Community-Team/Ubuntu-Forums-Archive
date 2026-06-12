---
title: "MySQL datadir and systemd"
date: 2016-05-01
forum: General Help
---

### Post by Keith_Helms on 2016-05-01
It seems to be getting harder and harder to move the mysql database directory (datadir).  A few releases back, apparmor came in the picture and I had to remember to go into **/etc/apparmor.d/usr.sbin.mysqld** and change the datadir there so mysql was allowed to use the new directory.

Now with systemd there is apparently a script I have to modify.  In order to get mysql to start I had to edit **/usr/share/mysql/mysql-systemd-start** and change the tests for the database directory to use the new directory.

This seems like a clumsy way to go about this, so I'm wondering if there is some command that does this change for me.  What is the recommended way to tell systemd where to look for the mysql database directory?

---

### Post by SeijiSensei on 2016-05-02
Maybe an easier solution is to add a symbolic link from /var/spool/mysql to the location where the database resides.

```

cd /var/lib
sudo mv mysql mysql.old
sudo ln -s /path/to/the/mysql/root/ mysql

```

---

### Post by tcagle53 on 2016-06-25
Thanks for this simple suggestion. I was looking at tons of misguided advice on monkeying with apparmor and wads of other stuff that is better left undisturbed it would seem.

---

