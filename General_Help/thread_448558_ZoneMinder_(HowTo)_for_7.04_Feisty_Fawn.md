---
title: "ZoneMinder (HowTo) for 7.04 Feisty Fawn"
date: 2007-05-19
forum: General Help
---

### Post by nami on 2007-05-19
I am trying to follow the following (supposedly) simple guide but I'm not getting anywhere.

[http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04](http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04)

I downloaded the deb file, double clicked it and let it install everything it wanted to.  When it finished, I can see no zoneminder anywhere in the main menu.

In the guide it says do the following:
> 
had to link the apache.conf file to zoneminder.conf per the readme.deb :-

/etc/zm/apache.conf to /etc/apache2/conf.d/zoneminder.conf 

what does that mean?

---

### Post by nami on 2007-05-21
*bump*

---

### Post by flat4 on 2007-06-15
working in getting mine setup will let you know

---

### Post by jethro10 on 2007-06-18
> **nami said:**
> I am trying to follow the following (supposedly) simple guide but I'm not getting anywhere.

[http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04](http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04)

I downloaded the deb file, double clicked it and let it install everything it wanted to.  When it finished, I can see no zoneminder anywhere in the main menu.

Have another look at [http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04](http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04) , the wiki's been updated since your question and its more informative.

For the link, just type it into a terminal session
sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf

then type this, or re-boot :-
sudo /etc/init.d/apache2 reload

Zoneminder is all web based and is accessed via firefox, or similar, just look at the wiki entry.
I've put this in at work now, its much better than our previous software

J

---

