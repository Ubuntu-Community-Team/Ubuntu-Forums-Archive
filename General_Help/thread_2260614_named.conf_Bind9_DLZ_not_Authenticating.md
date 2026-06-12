---
title: "named.conf Bind9 DLZ not Authenticating"
date: 2015-01-13
forum: General Help
---

### Post by theonlytalkinggoat on 2015-01-13
I fought with bind9 dlz for about 16 hours, over the past 2 days and finally figured out that bind is not sending the password to mysql, specified in the named.conf file.

Here are some of the errors I was getting:

```

cd /var/log/mysql
tail -f mysql.log
78 Connect    root@localhost on bind9_dlz
           78 Connect    Access denied for user 'bind9'@'localhost' (using password: NO)
```
```

cd /var/log
tail -f syslog
Jan 13 08:21:39 ubuntu named[16557]: Loading 'Msql zonev' using driver mysql
Jan 13 08:21:39 ubuntu named[16557]: mysql driver failed to create database connection after 4 attempts
Jan 13 08:21:39 ubuntu named[16557]: SDLZ driver failed to load.
Jan 13 08:21:39 ubuntu named[16557]: DLZ driver failed to load.
Jan 13 08:21:39 ubuntu named[16557]: loading configuration: failure
Jan 13 08:21:39 ubuntu named[16557]: exiting (due to fatal error)

```

Here was the configuration I used:

```
dlz "Msql zonev" {
   database "mysql
   {host=127.0.0.1 port=3306 dbname=bind9_dlz user=bind9 password=******}
   ...
```

I found this configuration on several websites, including this one.
[http://ubuntuforums.org/showthread.php?t=1867237](http://ubuntuforums.org/showthread.php?t=1867237)

I verified it was actually sending an attempt to communicate, by running 

```
tcpdump -i lo port 3306
```, 

while attempting to start the bind9 service. I got ```
localhost.58650 > localhost.mysql:
```. 

Of course, this assumes your mysql database is listening on 3306. I verified that by 
```
netstat -na | grep 3306
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
```

I verified I wasn't running chrooted, by looking at the bind9 init script in /etc/init.d/

```
# for a chrooted server: "-u bind -t /var/lib/named"
# Don't modify this line, change or create /etc/default/bind9.
OPTIONS=""
```
Then /etc/default/bind9
```

# run resolvconf?
RESOLVCONF=no

# startup options for the server
OPTIONS="-u bind -n 1"

```
Finally, today, having figured out that bind is not sending the password, I was looking for the official bind9 mailing list, and happened to come across their DLZ manual page, on sourceforge. [http://bind-dlz.sourceforge.net/mysql_driver.html](http://bind-dlz.sourceforge.net/mysql_driver.html) If you scroll down to the section that says, "The third line: **{host=localhost dbname=dns_data ssl=tRue}" **Under that, about 2 paragraphs down, are all the configuration options the host statement takes. The "password=" statment has been changed to "pass=" As soon as I eliminated the extra characters, guess what??? It started working with a password.

I hope this helps someone...

---

