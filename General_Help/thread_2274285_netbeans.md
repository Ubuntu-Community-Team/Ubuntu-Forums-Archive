---
title: "netbeans"
date: 2015-04-19
forum: General Help
---

### Post by yazvoprosywebw on 2015-04-19
Installed according to instructions - [netbeans]("https://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html")


how to start a program to open the interface?

p.s. recommend More php debugger for ubuntu

---

### Post by Dragonbite on 2015-04-20
Are you asking how to start Netbeans in Ubuntu?

Are you using Netbeans for Java or PHP development?

I am using [Netbeans's HTML5 & PHP]("https://netbeans.org/downloads/index.html") bundle for PHP development and use [Apache Friend's Xampp]("https://www.apachefriends.org/index.html") to set up the LAMP stack for easy turn-on and turn-off of the Apache & MySQL (and it comes with phpMyAdmin too). There are some installation instructions [here too]("https://netbeans.org/community/releases/80/install.html"). I'm also using OpenJDK on the system, not Oracle Java. 

When I want to develop, I first start Xampp, and the Netbeans from the main menu.

Only other thing I do is create a symlink between my local location of the files (so it is auto-synchronized with my cloud-based storage) and the /htdocs directory Xampp uses for its websites ```

cd /opt/xampp/htdocs
# sudo ln -s <website> /home/<username>/<directory to source code>
# or in my case
sudo ln -s ./auction /home/drew/Dropbox/Code/auction
```

---

