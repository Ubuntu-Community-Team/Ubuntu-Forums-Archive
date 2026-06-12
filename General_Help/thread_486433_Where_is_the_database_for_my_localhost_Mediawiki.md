---
title: "Where is the database for my localhost Mediawiki?"
date: 2007-06-28
forum: General Help
---

### Post by Jiawen on 2007-06-28
I installed localhost-only Mediawiki a couple weeks ago to create a wiki for one of my projects. It's working quite well. I now want to move the database for various reasons. I can't figure out where the database actually resides, though. 

I used [this installation]("http://linse.org/blog/2007/02/installing-mediawiki-under-ubuntu.html"), if that helps.

Thanks!

---

### Post by Brucevdk on 2007-07-04
Take a look at *LocalSettings.php* and the variables $wgDBserver, $wgDBname and $wgDBtype. If it's a MySQL database I guess you could [dump it]("http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html").

---

