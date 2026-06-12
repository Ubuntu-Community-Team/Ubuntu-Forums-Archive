---
title: "Subdomains minor problem."
date: 2013-01-28
forum: General Help
---

### Post by Novice2013 on 2013-01-28
Hello,
Since a few days I have an Ubuntu Virtual Private Server.
I use the /var/www/ directory to store my websites.
I placed my Joomla website in /var/www/personal/.
The Joomla websites doesn't generate any error messages, and the websites almost shows fine, except the Artisteer 4.0 Joomla slides aren't displayed properly.
When I go to my website via [http://ip-number/personal/](http://ip-number/personal/) then the slides show, however when I go to the website via [http://www.personal.mydomain.nl](http://www.personal.mydomain.nl) then the slides aren't visible.
While the source code of this website is identical no matter which of the two routes you take to get there.
In the error log I get this line many times:
[Sat Jan 26 21:02:37 2013] [error] [client ipnumber] File does not exist: /var/www/personal/personal, referer: [http://personal.mydomain.nl/](http://personal.mydomain.nl/)
Can anybody help me? How do I fix this?

---

### Post by ghost1227 on 2013-01-28
apache config would help...

---

### Post by sandyd on 2013-01-28
> **Novice2013 said:**
> Hello,
Since a few days I have an Ubuntu Virtual Private Server.
I use the /var/www/ directory to store my websites.
I placed my Joomla website in /var/www/personal/.
The Joomla websites doesn't generate any error messages, and the websites almost shows fine, except the Artisteer 4.0 Joomla slides aren't displayed properly.
When I go to my website via [http://<removed ip>/personal/](http://<removed ip>/personal/) then the slides show, however when I go to the website via [http://www.personal.aljowijnands.nl](http://www.personal.aljowijnands.nl) then the slides aren't visible.
While the source code of this website is identical no matter which of the two routes you take to get there.
In the error log I get this line many times:
[Sat Jan 26 21:02:37 2013] [error] [client <removed ip>] File does not exist: /var/www/personal/personal, referer: [http://personal.aljowijnands.nl/](http://personal.aljowijnands.nl/)
Can anybody help me? How do I fix this?
Its been quite a long time since ive used Joomla, however, 
there is an option in Joomla to set the url. Just set it to your domain instead of the ip.

---

### Post by Novice2013 on 2013-01-28
> **ghost1227 said:**
> apache config would help...
 
What makes it hard is that the website, the texts, the jpg-s and so on all display correctly. Only the Artisteer 4.0 slides aren't displayed.
 
Where can I change the line /var/www/personal/personal/ ? It needs to be /var/www/personal/
 
I entered the apache2 personal file correctly I think...

---

### Post by Novice2013 on 2013-01-28
The problem is the Artisteer 4.0 Template Editor, the path to the slides is incorrect.
Artisteer is aware and will try to fix this.

---

