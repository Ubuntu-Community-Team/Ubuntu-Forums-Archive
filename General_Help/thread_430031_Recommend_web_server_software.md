---
title: "Recommend web server software?"
date: 2007-05-01
forum: General Help
---

### Post by wordsmithereens on 2007-05-01
Hi all;

I've recently converted 2 Windows machines to Linux, and I'm considering converting my webserver as well. 

The site mainly consists of vanilla HTML pages, with bits of javascript here and there - nothing fancy, and the main load is from serving the pages and some downloads. The page hits per day vary from about 1000 to 3000 - rarely more and rarely less. 

Would Apache be overkill on a simple system like this, or would there be a webserver more suited to this use? It's currently running 2003 Server with IIS 6.

Thanks for any recommendations!  :) 

~ wordsmithereens ~

---

### Post by IcemanV9 on 2007-05-01
Heck no! It is not overkill. In fact, Apache(2) is a perfect fit. Use the server edition of Ubuntu. And, LAMP (Linux, Apache, MySQL and PHP) option would be _ideal_ to install. You'll love it once it's up and running. :)

---

### Post by wordsmithereens on 2007-05-01
Thanks for the info. 

 I know I wouldn't need the MySQL or PHP portions - at least not now. I imagine they can be toggled off to reduce the server footprint? 

I'm downloading the Feisty Server version now and will run it for a while in VMWare so I can get used to it. 

~ wordsmithereens ~

---

### Post by IcemanV9 on 2007-05-02
Just install server. And, when it's up and running, install [[COLOR="Orange"]**apache2**[/COLOR]]("https://help.ubuntu.com/community/ApacheMySQLPHP").

```
sudo aptitude install apache2
```

Check the wiki if you need more information.

---

