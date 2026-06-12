---
title: "phpmyadmin not showing gui on localmachine"
date: 2014-01-21
forum: General Help
---

### Post by Martin_Toye on 2014-01-21
Hey all got a strange problem

If i go to the physical server and point the browser to [http://localhost/phpmyadmin](http://localhost/phpmyadmin).

The page loads up but with out the GUI. all it displays is the code itself

Now if i go to another machine within the network and point the browser to [http://192.168.1.74/phpmyadmin](http://192.168.1.74/phpmyadmin)

everything displays fine no problems. 

Don't know if its worth mentioning on the server i am using firefox and on the other machine google chrome.


Any help is much appreciated. 

Thanks

Martin
(newcomer to linux and ubuntu)

---

### Post by dragonfly41 on 2014-01-21
Your URL string will be case sensitive .. try this [http://localhost/phpMyAdmin/](http://localhost/phpMyAdmin/)

---

### Post by Martin_Toye on 2014-01-21
No luck on the case sensitive side.

---

### Post by SlidingHorn on 2014-01-21
Can you post the contents of your /etc/hosts file?

---

