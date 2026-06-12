---
title: "Apache and perl"
date: 2005-08-21
forum: General Help
---

### Post by Chris Cromer on 2005-08-21
Alright after some playing around I was able to get apache and php installed and working. But when I tried to get perl running I ran into a few problems.

Now what I want is for perl to work outside of the cgi-bin. My apache is setup for multiple users, and handles it automatically. When you go to [http://localhost/](http://localhost/) it connects to /var/www/. When you go to [http://localhost/~chris/](http://localhost/~chris/) it connects to /home/chris/public_html/.

Now I need for .cgi and .pl scripts to work outside of the cgi-bin for both my regular localhost content, and my user based sites as well.

I will be honest, php and apache I was able to get working thanks to the fact the package manager in ubuntu was able to install them and configure them together. So  I don't know anything about how I got those 2 to work together. The only configuration I have messed with was in php to make it connect to sqlite and mysql.

Oh and I defaintly don't want mod perl. Most of my scripts don't work with it out of the box. I want it to run as cgi.

Anyway, thanks in advance for any help, tips, or anything you can give me.

---

### Post by Chris Cromer on 2005-08-24
Alright well I was able to get perl to work the way I want now. But I ran into another wall. I am migrating from windows and this is my first time using linux... so I am a noob to this whole linux thing.

In windows I would normally use ppm(perl package manager) which came with perl to install packages like dbi, mysql, md5 and other such things... but I don't see any ppm script in /usr/bin/ with perl... so either it's in another location, or there isn't any such thing in linux. So how do I install packages into perl?

---

### Post by zgolus on 2005-08-25
it's called cpan in linux - Comprehensive Perl Archive Network and it's located in /usr/bin/cpan; works much the same way as ppm does;

---

