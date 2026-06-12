---
title: "mysql socket problem"
date: 2006-07-21
forum: General Help
---

### Post by viniosity on 2006-07-21
I did a restart of my server and all of a sudden mysql won't start.  I get this error when I try to start it manually:
```

Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

Of course, mysqld.sock doesn't exist anywhere.  I googled around and found that renaming the /etc/mysql/my.cnf file to something else and then starting mysql fixes the issue.  And it does..

I figured that maybe the my.cnf file was corrupt, so I copied it from another server but no matter what when I have a my.cnf file I get the above error.  

Any idea why that started happening all of a sudden and what I can do to fix it?  Is it dangerous to run my server's mysql 
without a my.cnf file?

[edit: bah, it was a permissions issue with /var/log/mysql being wrong.  After I fixed it to mysql:adm it works.]

---

### Post by thor918 on 2006-08-10
viniosity, thanks. That fixed my problem!
the logfiles and all of the mysql database files where owned by www-data user. hmm strange...
changed them back to mysql user fixed all :)

---

