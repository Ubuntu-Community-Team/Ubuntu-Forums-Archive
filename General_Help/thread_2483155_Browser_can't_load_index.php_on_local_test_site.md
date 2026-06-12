---
title: "Browser can't load index.php on local test site"
date: 2023-01-21
forum: General Help
---

### Post by nickdc on 2023-01-21
[SIZE=3]I'm running Ubuntu 22.04 on VirtualBox, itself running on Ubuntu Mate 22.04. Following various online guides I've successfully installed the LAMP stack (using MariaDB rather than MySQL) and configured it to run two test sites with the following directory structure: /var/www/html/mysite_1/public_html   and   /var/www/html/mysite_2/public_html.  I've created a simple index.html file for each site, placed them in the respective public_html folders and they load correctly in the browser (Firefox) using addresses mysite_1 and mysite_2, so I conclude the basic set up is sound.

But one of the sites I want to test uses php and its home page is launched by index.php. When I removed the test index.html file from the public_html folder for that site and copied all the files for the test website, the browser just showed a blank page. After more troubleshooting searching I tried adding ```
DirectoryIndex index.php index.htm
``` to the apache2.conf file. After restarting apache this changed the behaviour, and instead of a blank page I got:[/SIZE]
[SIZE=3][B]
Warning[/B]:  Unknown: Failed to open stream: Permission denied in **Unknown** on line **0**

**Fatal error**:  Failed opening required '/var/www/html/[mysite_1/public_html/index.php]("http://diclay.co.uk/public_html/index.php")' (include_path='.:/usr/share/php') in **Unknown** on line [B]0

[/B]I've googled this and read a lot of posts but found nothing that works for me. I'm also concerned as a lot of the posts are very old now - there's not much from the last year or two. Hence my coming here for help, as I'm at the stage where I fear any more attempts to tweak config files could make matters worse and I'm at the limits of my understanding how it all fits together when running two sites on the same server. I suspect it's just a simple edit somewhere that I need to make, but what, and where?[/SIZE]

---

### Post by nickdc on 2023-01-22
My silly mistake: I hadn't checked permissions after copying the website files into the public_html folder! A simple chmod and it's working....with some glitches on other pages, but I've been there before and should be able to sort.

---

