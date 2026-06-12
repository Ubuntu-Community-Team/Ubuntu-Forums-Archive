---
title: "I want a LAMP server, but only sometimes!"
date: 2007-05-21
forum: General Help
---

### Post by Mr. Picklesworth on 2007-05-21
I have a really slow and clunky computer that I use for lots of miscellaneous tasks. Recently, I have wanted to use it as a LAMP server for some basic testing and development, and so I installed the right packages and configured it how I like it. (Each web site gets its own user account in the testsite group with its own home folder - resulting in instant FTP access to that folder - then a cronjob takes care of creating a subdomain for that site and a MySQL user. It's really quite overkill - I'm not running a web host or something, so it would be surprising if there's a single new site in a month - but it just feels nice).

Now, the problem: This thing starts up when I boot the computer and causes noticeable slowdown when I want to do stuff that has nothing to do with the web server.
What steps should I take if I want this web server to only run when I tell it to (eg: when a certain user logs in)? The trick is that I can't be bothered to restart my computer, or I may want to keep using my Ubuntu desktop while the server is up.

---

### Post by Canuckelhead on 2007-05-21
Use this one... follow the instructions... you can start and stop lamp whenever you like...
[http://www.apachefriends.org/en/xampp.html]("http://www.apachefriends.org/en/xampp.html")

---

