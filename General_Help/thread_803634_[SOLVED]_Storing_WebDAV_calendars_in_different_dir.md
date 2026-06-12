---
title: "[SOLVED] Storing WebDAV calendars in different directories"
date: 2008-05-22
forum: General Help
---

### Post by ntalamai on 2008-05-22
Hello, 

I have managed to install webdav calendar using the guide on:
[http://ubuntuforums.org/showthread.php?t=119228](http://ubuntuforums.org/showthread.php?t=119228)

However, in that guide the calendar files are stored in /var/www/devhome/

How do I need to change the /etc/apache2/mods-enabled/dav_fs.conf in order to point to a different directory? For example /home/user/calendars?

I am assuming that dav_fs.conf is the correct place to go, because I recently configured webdav + svn in my server, and this information is stored in dav_svn.conf file and the "command" in the file looks like:
SVNPath /home/user/svnrepository

I am sure there must be a similar "command" for dav_fs.conf, but I cannot find it on the net.

Do you know how to do it? Thanks!

---

### Post by ntalamai on 2008-05-23
It had to do with permissions. Solved. The rest is here: [http://ubuntuforums.org/showthread.php?t=803893](http://ubuntuforums.org/showthread.php?t=803893)

---

