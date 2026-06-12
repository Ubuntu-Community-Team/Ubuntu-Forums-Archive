---
title: "Installing PHP5"
date: 2006-11-27
forum: General Help
---

### Post by Kerry Lange on 2006-11-27
Hi there:

I've used the synaptic package manager to install Apache 2 and I've also installed PHP 5.  However, when trying to load a page, I'm offered the choice of choosing a program to view the file with or save the file.  Obviously, I've not got it installed correctly.

I see using the system monitor that Apache is running but I see no files related to PHP running.

My goal is to have Apache, PHP, & MySQL running on my machine so I can use it to develop web apps & sites.  I'm not serving up any pages and have no intention of doing so.

Anyone have any tips?

---

### Post by ~LoKe on 2006-11-27
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PHP5](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PHP5)

---

### Post by Kerry Lange on 2006-11-27
Worked like a charm and the php info file displays as it should.  Thanks!

However, when I try loading any php file from a directory below the www, say "www/bhmp/" I still am invited to pick a program to load the file or a place to save it.  Is there a setting in the "php.ini" file I need to change?

---

### Post by Kerry Lange on 2006-11-27
Okay, it *is* working.  I tried simply loading the "index.php" file by referencing the root of the site directory "www/bhmp/" without the file name.  I guess that's a setting in Apache I have to change so that it looks for "index.blah" when referencing a directory.

---

