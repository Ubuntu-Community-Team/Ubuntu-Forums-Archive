---
title: "Ubuntu Server 14.04 nginx Wordpress?"
date: 2016-06-05
forum: General Help
---

### Post by albert41 on 2016-06-05
I was wondering if someone could shed some light on what im missing?
  So before I was running my own small website on WAMP on windows now  that Im moving everything to linux I installed ubuntu server and I set  up LEMP using this tutorial [http://www.tecmint.com/setup-lemp-phpmyadmin-on-ubuntu-15-04/](http://www.tecmint.com/setup-lemp-phpmyadmin-on-ubuntu-15-04/)  So i uploaded the sql backup from my previous phpmyadmin on WAMP and uploaded to the new server no issue there.
  Here is where im stuck so i have the backup of the wordress www folder and I placed it /var/www/html
  I guess what im really stuck is where does nginx pulls wordpress information?
  
this is my nginx default file [http://pastebin.com/iTj05N67](http://pastebin.com/iTj05N67)

  I can connect to my site mydomain.com no issue there but when I click on the site that connects to another page it shows the 404
  But now theres another issue lets say i click on a link the site it shows the 404 not found :(
  [http://postimg.org/gallery/b70ppwi4/](http://postimg.org/gallery/b70ppwi4/)
  Thank you


EDIT: SOLVED THE issue was because I was on apache before and nginx does not read the same stuff i had to add try_files $uri $uri/ /index.php?$args; on the default file of nginx to look something like this 

location / {
            try_files $uri $uri/ /index.php?$args;
}

---

