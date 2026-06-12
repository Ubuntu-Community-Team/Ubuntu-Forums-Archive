---
title: "phpmyadmin not working"
date: 2008-02-28
forum: General Help
---

### Post by Liesmith Loki on 2008-02-28
Okay. I tried posting in other threads, but haven't gotten any answer yet, so I'm making a new thread. Sorry if that's bad. Anyway, I did my share of research and looking through threads and such, but I still have this problem.

Initially the problem was that phpmyadmin was not working when I would access it from [http://localhost/phpmyadmin](http://localhost/phpmyadmin). It said that it could not find the page, and that was because it was not installing into /var/www and instead was in /usr/share.

Looking in the threads here, someone said that to fix it, I should create a symbolic link from /usr/share to /var/www. This only messed up my problem more. Now when I try to access [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it tries to download a random phtml file. (This problem is also referenced [here]("http://ubuntuforums.org/showthread.php?t=621014") by another user.)

Then I read that the problem was that I needed to reconfigure my phpmyadmin to configure apache2. I facepalmed, since I knew that's what started this problem. So I deleted the symbolic link (as best I could), and reconfigured phpmyadmin, making sure that apache2 was checked with an asterisk in the dialog box. 

I try it again... It still tries to download a random phtml file even though I deleted the link. By the way, I've uninstalled and reinstalled LAMP multiple times throughout this process, but still to no avail. I've restarted apache2 a number of times as well. Still doesn't work.

I need major help here. D:

---

### Post by Liesmith Loki on 2008-02-28
Erp. Nevermind... Ignore this. I realized I just had to clear my cache. xD

---

