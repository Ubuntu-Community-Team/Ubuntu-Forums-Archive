---
title: "php"
date: 2007-06-07
forum: General Help
---

### Post by seismicmike on 2007-06-07
I followed all the instructions [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") to set up LAMP on my laptop, and it works to the degree that /var/www/index.html shows up when I type [http://localhost](http://localhost)

but if it's /var/www/index.php, firefox asks me if I want to download it instead of running it in my browser.

I'm not to worried at this point about getting my page up online - this computer isn't even going to be my server it's just for development of my app I'm going to be making.

I have 2 theories:

1) I have something wrong with my php5 install

2) somehow I didn't properly alert apache of php's existence

Thank you in advance for whatever help you can render.

---

### Post by seismicmike on 2007-06-07
PS. mysql works - I went in through konsole and added the database, tables and such

also, I'm not actually running ubuntu (if it matters). I am running MEPIS Linux b/c it's the only distro that would configure my wireless and sound (I'm on a laptop), but I love the community here, so I figure I should at least post the question here - and I also figure that it really shouldn't matter for LAMP which distro I use, right?

---

### Post by Mr. C. on 2007-06-08
Be sure that 

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

are somewhere in your apache config files.

The troubleshooting guide also shows:

> Troubleshooting

Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. Be sure to clear your browser's cache before testing your site again. 

MrC

---

