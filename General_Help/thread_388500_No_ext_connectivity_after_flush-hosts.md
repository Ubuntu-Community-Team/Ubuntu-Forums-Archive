---
title: "No ext connectivity after flush-hosts"
date: 2007-03-19
forum: General Help
---

### Post by silurius on 2007-03-19
[I]Ubuntu Edgy (Linux 2.6.17.11)
MySQL 5.0.24a
Apache/1.3.34 Server[/I]

[indent]1. I can reach static html content on my site, both externally and internally, with no issues.  This has always been and still is the case.
2. Any PHP page I attempt to load (locally or externally) seems to ask Firefox to open a "PHTML file"  in an external application.
3. Although I don't normally use it, MySQL Administrator gui seems to be struggling with something.  It will not close gracefully at all and will occasionally crash while I'm browsing around in the tool.  Since I wasn't using it much before this issue, I do not know if it had problems before or now (I inherited this supposedly-relatively-clean Edgy box from a co-worker).[/indent]

This problem began last week while I was troubleshooting a different issue.  At that time, my web server was able to access my database just fine and I could reach my sites without issue.  But I was unable to access mysql remotely, probably due to the initial setup.

While trying various things to get things working, at one point I ran the following command after reading [a KB article]("http://dev.mysql.com/doc/refman/4.1/en/flush.html") that seemed to be applicable to my issue.

> mysqladmin -u root -p flush-hostsMy thinking was that I had somehow locked out my host due to multiple bad passwords or bad syntax or some such, and that this would reset me and allow me to continue troubleshooting.

Immediately after doing this, my web site could no longer talk to MySQL.  Even stranger, some basic site functionality was failing too.  A static html page at the root loaded fine, but Drupal PHP content would not.  Normally with a DB problem, a Drupal site will at least display a simple PHP page and report there that it can't connect to the database.  In this case, the browser hits index.php and attempts to download it (giving it the name "ii9tzam3" - Firefox reported this as being an "application/x-httpd-php" type file).

So I think my flush-hosts command may have borked Apache in some way.  After multiple reboots and a few troubleshooting steps taken from [this thread]("http://www.ubuntuforums.org/showthread.php?p=2309181#post2309181"), I found myself facing a brick wall and considering wiping clean and starting over.

Even stranger, the MySQL Administrator gui seems to be struggling with something.  It will not close gracefully at all, and will occasionally crash while I'm browsing around in the tool.  Since I wasn't using it much before this issue, I do not know if it had problems before or now (I inherited this supposedly-relatively-clean Edgy box from a co-worker).

I have backups of all my databases, so I can probably go from a restore if I need to do anything environmental.

I'm pretty green to most aspects of this situation and am learning as I go.  Would appreciate any feedback whatsoever, before I decide to start uninstalling/reinstalling various components.

*edited for clarity*

---

### Post by silurius on 2007-03-19
I shall probably commence uninstalling/reinstalling MySQL in the morning.  I'll be sure to check here and abort, if I see any suggestions or input.  (I prefer to understand what's under the hood when this sort of thing happens, but I'm also running out of time).

---

### Post by silurius on 2007-03-19
Well, I bit the bullet and reinstalled.  The MySQL Administrator error below has to be an important clue:

> *(*delete my.cnf*)*
[B]sudo aptitude remove mysql-server
sudo aptitude install mysql-server[/B]
*(*reboot*)*
**mysqladmin -u root -p start**
Enter password: 
**[COLOR="Red"]mysqladmin: Error starting slave: The server is not configured as slave; fix in config file or with CHANGE MASTER TO[/COLOR]**
*(*restored my.cnf, same result in mysqladmin*)*

Clueless as to what the error means.  Situation the same. Can get in via MySQL Administrator & MySQL Query Browser, but cannot access over http on localhost or from a machine on LAN.

I even installed Firestarter and left it on to see if anything would show up in the logs, but failed to learn anything new and turned it off again.

If my searches continue to not turn anything up, I may wipe the server and reinstall everything.

---

