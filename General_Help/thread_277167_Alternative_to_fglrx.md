---
title: "Alternative to fglrx"
date: 2006-10-14
forum: General Help
---

### Post by Architeuthis on 2006-10-14
I have an ati radeon 9250, but ati stopped supporting my card, this is not good because the latest driver for my card contains some irritating bugs which makes a particulary program crash (spring [www.taspring.clan-sy.com)](www.taspring.clan-sy.com)). Someone in the #ubuntu channel told me i should try sudo dpkg-reconfigure xserver-xorg, does this give me a full replacemt of fglrx and will it enable openGL? If i do sudo dpgk-reconfigure xserver-xorg, isnt that what ubuntu does during the installation or is it different?

---

### Post by Ramses de Norre on 2006-10-14
That is indeed done when you install ubuntu, the command will allow you to change all X settings.
You wont be able tp 'generate a new fglrx' but you'll be able to reset all settings or choose another driver.
(allready tried the open source 'ati' or 'radeon' drivers?)

---

### Post by podunk on 2006-10-14
I've decided my solution is spelled
 N v i d i a. 

I mean, my card isn't that old, and it sort of aggravets me that they don't support it any more.

You might try the how to to install and tune your driver on this page:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

If you are using Dapper then chose method 1 on the Dapper page.

---

### Post by Architeuthis on 2006-10-14
Thanks for the reply

(allready tried the open source 'ati' or 'radeon' drivers?)
I dont know exactly what you are talking about: do you mean selecting ati or radeon with sudo dpkg-reconfigure xserver-xorg? Or are you talking about someting else?

-You might try the how to to install and tune your driver on this page:
[http://wiki.cchtml.com/index.php/Ubuntu:](http://wiki.cchtml.com/index.php/Ubuntu:) thats my current driver which has bugs, i am searching an alternative to this

---

### Post by dagnabit dang doohickey on 2006-10-14
The driver version used in Method 2 on [the unofficial ATI Linux Driver Wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") doesn't support your card. The wiki uses version 8.29.6, but you need version 8.28.8.

You can go to the [ATI driver downloads]("http://www.ati.com/support/driver.html") to get the 8.28.8 driver installer or use:
[URL="https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run"]
this direct download link to the ATI 8.28.8 driver installer[/URL]

and then follow Method 2 on the wiki.

---

### Post by Architeuthis on 2006-10-15
The 8.28.8 is my current driver which contains bugs!

I found out i can select the open source radeon driver by changing "ati" with "radeon" in the device section with sudo gedit /etc/X11/xorg.conf. But it doest seem to enable openGL.

---

