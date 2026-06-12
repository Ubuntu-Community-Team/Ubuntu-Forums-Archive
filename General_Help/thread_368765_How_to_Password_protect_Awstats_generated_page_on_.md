---
title: "How to Password protect Awstats generated page on apache2?"
date: 2007-02-23
forum: General Help
---

### Post by mikestefff on 2007-02-23
Hi, my VPS is running apache2 with awstats. To view my statistics I currently have to enter this url:

[http://www.mysite.com/awstats/awstats.pl?config=www.site.com](http://www.mysite.com/awstats/awstats.pl?config=www.site.com)

This means that anyone can do this to view my sites stats. How can i password protect this, or any other measures that would make me the only person able to view it? Since its a VPS, I cannot use .htaccess to allow only from 127.0.0.1

Any ideas?

Thanks

---

### Post by Sherman.Boyd on 2007-03-09
Use apaches realm security:

[http://www.aaronsw.com/2002/howto/passwords](http://www.aaronsw.com/2002/howto/passwords)

---

