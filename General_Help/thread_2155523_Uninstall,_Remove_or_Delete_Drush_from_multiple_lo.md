---
title: "Uninstall, Remove or Delete Drush from multiple locations"
date: 2013-06-18
forum: General Help
---

### Post by agentofcode on 2013-06-18
Prior to discovering the [recommended method of installing Drush]("https://drupal.org/node/1248790") I attempted to install it the standard Ubuntu way via the **Software Center **and** sudo apt-get install drush**. Now I have two non functional Drush installs in two diff. locations. I would like to remove both of them so I can follow the recommended directions and get Drush installed correctly.

One location of the install is **/usr/share/php/drush** the other is [B]/drupal/drush

[/B]I've tried **sudo apt-get remove drush** and **sudo apt-get autoremove drush **which are commands I found on other threads. I also tried removing it from the **Software Center**. But I still have two installations of drush. Any help is greatly appreciated, thanks!

---

### Post by ajgreeny on 2013-06-18
The link you give says that the way to install is:-
> Drush can easily be installed on Ubuntu by using Aptitude or apt-get.  If you have sudo rights the quickest way to install Drush is from the  Ubuntu repository:

 $ sudo apt-get install drush

which is basically the same as using the software centre, so I do not understand what your problem is exactly, though you say you now have two installations of drush.  Have you carried out the self-update and rebooted as the link suggests?

---

### Post by agentofcode on 2013-06-18
I did try that previously. Couldn't get it to work. Decided to try it again since you brought it up and I got the update to work and now the version reports back as being updated. However I still have an install at **/drupal/drush**. How can I get rid of this second install? I'm not sure what method of install placed it there. But I do not recall ever selecting where I wanted it installed.

---

### Post by 3rdalbum on 2013-06-18
sudo rm -rf /drupal/drush

---

### Post by agentofcode on 2013-06-18
Thanks! That's all I needed.

---

