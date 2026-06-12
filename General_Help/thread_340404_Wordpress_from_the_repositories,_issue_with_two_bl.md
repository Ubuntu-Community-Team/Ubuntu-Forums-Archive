---
title: "Wordpress from the repositories, issue with two blogs"
date: 2007-01-17
forum: General Help
---

### Post by pasipasi on 2007-01-17
I installed Wordpress from the repositories, used a sql dump from my previous blog and got it working. I didn't even run the install.php script that came with it. Then I decided to host my friend's blog too, because it seemed to be so easy. My friends blog uses the same database, so I made just made a copy of the files and changed the prefix in wp-config.php. The blog started working.

Then I noticed my own blog isn't working anymore. It would seem that whenever I change one of these wp-config.php files, every one changes. I have no idea why. Both blogs are pointing to /etc/wordpress/wp-config.php for the config, is it possible to make them point to their own config-files, thus being able to use different part of the database?

---

### Post by pasipasi on 2007-01-18
Problem fixed. Installing wordpress from the repositories downloads a copy of the files to /usr/share/wordpress and makes a link to /etc/wordpress/wp-config.php. I removed the link and all the blogs started working nicely.

---

