---
title: "mpd &amp; gmpc"
date: 2005-04-20
forum: General Help
---

### Post by woifi on 2005-04-20
hi folks!

... just installed mpd (music player daemon) and gmpc (gnome music player client). i made a conf file in my home directory and a database file by mpd --create-db.

then i started gmpc and connected to the server. unfortunately there are no files in the playlist and gmpc says "gmpc - stopped" in his display.

any ideas?

bye

woifi

---

### Post by woifi on 2005-04-30
*push* ;)

---

### Post by Xgkkp on 2005-05-03
[QUOTE=woifi]*push* ;)[/QUOTE]
 try running 

/etc/init.d/mpd start

and it gives you a message telling you some command to run (as root) to configure it. It'll create a directory that you have to add symlinks into to get the music. You can then tell it to refresh the database. However, I have yet to get it to output any music, I think due to the fact that ubuntu uses esd.. I am working on finding a solution!

Edit: I got it working and posted a howto: [http://www.ubuntuforums.org/showthread.php?t=31763](http://www.ubuntuforums.org/showthread.php?t=31763)

---

