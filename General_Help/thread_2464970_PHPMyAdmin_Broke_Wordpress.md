---
title: "PHPMyAdmin Broke Wordpress?"
date: 2021-07-17
forum: General Help
---

### Post by Deanimator on 2021-07-17
For a while I've been thinking of doing a little database development using MySQL.

I've already got Wordpress running on an Ubuntu 20.04 server.

Thinking to make things a little easier, I decided to install PHPMyAdmin.

After installing it, my Wordpress installation is now inaccessible.  I can't get to it externally, and when trying to access it directly on the server, after an extended delay, I get nothing but dead links with no images.

The failure of Wordpress and the installation of PHPMyAdmin seem to coincide in time.

Is it possible that PHPMyAdmin broke Wordpress, and if so, how can I get it working again without killing PHPMyAdmin and reinstalling Wordpress (and PHP and MySQL) from scratch?

---

### Post by TheFu on 2021-07-18
I don't know, but suspect that there is a default DB setup in a php.ini file.  When it was just WP, then the WP DB file was the default. When you installed PHPMyAdmin, it probably changed the default DB somewhere.  I doubt anything was lost.  Just use your versioned backups to compare which files were modified before and after the problems.  Shouldn't be too hard.  You do have versioned backups, right?

Hopefully, these aren't available on the internet.  I see hundreds of PHPMyAdmin hacking attempts daily on my systems.  Hundreds.
```
$ egrep -ic phpmyadm /var/log/nginx/*g |grep -v :0
/var/log/nginx/splat.access.log:749
```
That's just today in the last 6 hours.

For wordpress attacks, it has been over 5300 in the same time period.

Just sayin'.  Be careful out there.  I don't use either WP nor PHPMyAdmin, so there's no reason anyone would ever connect to my servers looking for those tools.

I'd use **locate** to find all the possible different php.ini files.  There are 21 of those files on my wallabag and nextcloud server between the different versions of php and the different applications and apache.

---

