---
title: "update borks zimbra and gallery2, mysql"
date: 2007-02-22
forum: General Help
---

### Post by pksings on 2007-02-22
I ran updates this morning and now Zimbra and Gallery2 are producing mysql errors. Mysql appears to be running, but neither can get data from them. 

According to the logs I'm receiving mail but I can't get to it via POP, IMAP or the web client.

Gallery just gives me mysql errors about not being able to connect on the socket /tmp/whatever.

This is bad, very bad....

Help!?!

---

### Post by santo on 2007-03-04
I'm experiencing the same problems after having applied the latest upgrades.
Some of those updates were related to php5. Not sure about the others

Edit:
The exact error message when trying to access mysql from the command line:
```

# sudo mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)

```

---

### Post by pksings on 2007-03-04
One of the things I found is that mysql update and system user passwords got changed and can no longer start or update mysql without an error about it. 

I did a search and found a link that showed how to change those passwords and did, I think I searched on the mysql error.

That seemed to solve the mysql problems but by then I already had given up on zimbra and removed it and replaced it with Postfix and assp. No calendar anymore, I am of the opinion that none of them will work with my environment. OX works only with Redhat and it's clones,  Egroupware doesn't work at all, won't generate a config that runs, and Zimbra is basically un-supported, the "free" edition is apparently too fragile and I never got an answer on their forums in a four day period that solved the problem. If it was their commercial product I'm sure I would have gotten an answer in a hour or few. But I understand, it's business. And I couldn't go any longer without email, my wife was ready to have my head.  So I deleted it and went back to postfix just to get email functionality.

---

### Post by santo on 2007-03-05
Can you give me some more details about what you exactly did to get mysql working again (a link, some commands, ...)

As for the mail/groupware stuff:
I'm currently using Scalix Community Edition as my main mailserver / groupware app, which is free for up to 25 "enterprise" users (they get all the functionlaity) and an unlimited number of "normal" users (limited functionality).
Unfortunately, they don't officially support Ubuntu yet as the server platform (but installation guidelines for ubuntu are available throughout the forums and the wiki for the "RAW" edition I think)
Maybe you should take a look at it ?
[http://www.scalix.com](http://www.scalix.com)

Note: it's not as easy to install as zimbra (i.e. no antivir / antispam out-of-the-box, etc)

** EDIT **
Creating a symlink /tmp/mysql.sock works around the problem:
```

sudo ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock

```

Nevertheless it's still unclear why client apps try to access /tmp/mysql.sock instead of /var/run/mysqld/mysqld.sock (as configured in /etc/mysql/my.cnf)

---

### Post by pksings on 2007-03-05
To repeat the error I had, /etc/init.d/mysql stop, or start.
Do a google search of that error message, it will lead you to a number of posts that show how to change the mysql passwords.  I think I actually used a procedure from the Ubuntu forums but I did not keep any links.

---

### Post by soy Keymaster on 2007-12-13
I recently found out the cause of this error when trying to install Zimbra on Ubuntu 7.04 and noticing it handily borked everything else on my server.  There's a number of factors in play here:

1) Zimbra installs its own version of libmysqlclient to /opt/zimbra/lib/libmysqlclient.so.15
2) Due to the way ldconfig works on Ubuntu *everything on the server* that accesses a mysql server will end up linked to this library and *not* the official Ubuntu libmysqlclient.  Try this command to see what I mean: ```
ldd `which mysql` | grep libmysqlclient
```
3) Zimbra's version of libmysqlclient uses **/tmp/mysql.sock** as the default way to connect to the database
4) The recent versions of the the official Ubuntu mysql packages use **/var/run/mysqld/mysqld.sock**

So, given all that, you can see what happens.  Before Ubuntu's mysql packages was updated everyone was happily using **/tmp/mysql.sock**.  Then Ubuntu updated the mysql packages to start using **/var/run/mysqld/mysqld.sock** but only the server is using that because all of the client software is still linked against Zimbra's libmysqlclient which still uses **/tmp/mysql.sock**.

So far the easiest fix I can see is santo's suggested symlink solution:
```
sudo ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock
```

---

