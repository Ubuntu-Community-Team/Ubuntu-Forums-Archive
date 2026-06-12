---
title: "Transfering to Godaddy from Localhost"
date: 2007-09-23
forum: General Help
---

### Post by dadude on 2007-09-23
Hi guys,
Here's what I'm doing. I set up a joomla page on an ubuntu server and I have decided that the new best solution for me is to have Godaddy host my page. I already have joomla installed on the page and I'm following this tutorial to transfer everything over [http://hammokstudios.com/index.php?option=com_content&task=view&id=12&Itemid=36](http://hammokstudios.com/index.php?option=com_content&task=view&id=12&Itemid=36)
Now I'm having a problem getting my database exported from ubuntu. I cannot seem to get to myphpadmin page. I go [Http://localhost/phpmyadmin](Http://localhost/phpmyadmin) and just get the index of phpmyadmin which just contains a config file. So if someone could please help me out that would be great. Thanks in advance.

---

### Post by jamvegan on 2007-09-23
My apologies if this is a silly question, but did you ever uninstall phpmyadmin?  The reason that I ask is because there should be quite a lot of files in your phpmyadmin directory, but I believe that if you uninstall software without specifying complete removal, config files get left behind.  If you look at /var/www/phpmyadmin with ls do you see just the config file, or do you see a bunch of .php and .html files?  If all that's there is the config file, then installing phpmyadmin should solve your problem.

---

