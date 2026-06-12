---
title: "wordpress doesn't work"
date: 2006-08-30
forum: General Help
---

### Post by nix4me on 2006-08-30
Hi,

I followed this guide to install wordpress and it doesn't work.
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

When I go to [http://localhost/wordpress](http://localhost/wordpress), I see the wordpress help screen which says it can't connect to a database.

I have a fully functional lamp server and phpmyadmin is working fine.  It seems to me that those wiki instructions are incomplete or incorrect.

Any ideas?

nix4me

---

### Post by btdown on 2006-08-30
In those instructions, I dont see any entries where you import the sql tables into the database. I also dont see where it tells you to edit the config file to put your username, password and database name values. I would forget you ever saw that page.

I just installed Wordpress in a vmware server session a few days ago and used the instructions for installation here:

[http://codex.wordpress.org/Installing_WordPress](http://codex.wordpress.org/Installing_WordPress)

There are difference levels of install information available on that page. 

BT

---

### Post by peabody on 2006-09-02
[http://www.ubuntuforums.org/showthread.php?t=248823](http://www.ubuntuforums.org/showthread.php?t=248823)

My howto just got posted.  Perhaps it'll help, perhaps it won't.  It sounds like your problem might be that the config-hostname.php in /etc isn't named properly.  I go over this in my howto.

---

