---
title: "Getting started with mysql"
date: 2012-10-22
forum: General Help
---

### Post by psionman on 2012-10-22
I hope this is the right place

I gave installed mysql on Ubuntu 10.04 an I really need some help getting started

I tried >mysqld but got an error

Tried > sudo mysqld and the system does away for about 60 secs then comes back to  command prompt

I know I need some education, but where can I look?

---

### Post by sarloth on 2012-10-22
> **psionman said:**
> I hope this is the right place

I gave installed mysql on Ubuntu 10.04 an I really need some help getting started

I tried >mysqld but got an error

Tried > sudo mysqld and the system does away for about 60 secs then comes back to  command prompt

I know I need some education, but where can I look?

"mysql**d**" is the daemon which runs in the background. To simply interface with mysql either: download a mysql UI, use phpMyAdmin, or type "mysql" at the "$" prompt. Documentation for the mysql command prompt is available at the link below.

[http://dev.mysql.com/doc/refman/5.5/en/mysql.html](http://dev.mysql.com/doc/refman/5.5/en/mysql.html)

Please also note thatt the user-level prompt ends with "$". Root prompt (not readily available in Ubuntu) ends with "#". The mysql prompt will end with ">" as does Windows, I believe.

Out of curiousity: why such an old OS version?

---

### Post by Lars Noodén on 2012-10-22
mysql uses a client-server model.  You were trying to run the server.  You're right in that it does have to be running before you can use it via a client, but it gets started differently.  Try this:

```

sudo service mysql start
service mysql status

```

If you run the status line above and see that it is running, you are all set on that front.  Once the server is running, all your activities will be via a client.

sarloth pointed you to the client.

---

### Post by psionman on 2012-10-22
Thanks for your help

> **sarloth said:**
> 

Out of curiousity: why such an old OS version?

I'm running 10.04. Is that so old?

The 6.06 in profile I am not allowed to change

---

### Post by Lars Noodén on 2012-10-22
10.04 is not that old, there is [server support through April 2015](https://wiki.ubuntu.com/Releases).  That said, there is a newer Long Term Support release out, 12.04.  It will have a newer version of MySQL (5.5) or Postgresql (9.1) for you to work with.

---

### Post by sarloth on 2012-10-22
> **psionman said:**
> Thanks for your help



I'm running 10.04. Is that so old?

The 6.06 in profile I am not allowed to change

As was already answered, there are newer versions. But, to just add a little insight to version numbers and determining the age:

YY.MM is the version format, where YY is the last 2 of the year and MM is the month. Ubuntu releases every 6 months. These releases take place in April (YY.04) or October (YY.10) of each year. So a 10.MM would be at least 2 years old, 2.5 in your case.

If you are new to Linux, 2 years is like EONS :P

Welcome and enjoy! :)

---

