---
title: "Passwords in scripts"
date: 2017-11-28
forum: General Help
---

### Post by cc1984 on 2017-11-28
I'm a newbie when it comes to scripts. I run a Nextcloud installation on Ubuntu Server 16.04 and have written two scripts, one to backup the database and the other to backup the data folder and a few other things using rsync. I have been using these scripts for quite awhile and they work well. However, I would like to consolidate the two scripts and use cron to automate the process.

The question I have is, what is the best practice for handling passwords in a script? The database backup script requires a password to export the db using mysqldump. Right now I manually run the script and then input the password by hand. This server isn't exposed to the Internet but I would like to know what is a secure way to handle the password. I know I could just create a variable in the script and assign it the password but there has to be a better way to do this.

Thanks!

---

### Post by cc1984 on 2017-11-28
I found the solution for passing [passwords to a script for mysqldump]("https://dev.mysql.com/doc/refman/5.7/en/password-security-user.html"). Essentially the solution is to create a file to with the password in it. mysqldump has an option (--defaults-file) that you can point back to your file containing the password.

It looks like this:
```
mysqldump --defualts-file=pathtopwfile  dbname > destination
```

---

