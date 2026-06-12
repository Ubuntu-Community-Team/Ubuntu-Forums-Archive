---
title: "Installed Php Mailer Problems"
date: 2007-12-10
forum: General Help
---

### Post by ryjal on 2007-12-10
I installed a lamp server about 4 months ago, all was working fine PHP5, Appache2, MYSQL all working great. But I was developing some php pages that needed to send an email with attachments so I installed libphp-phpmailer, my test pages all seamed to work fine. I then noticed that all my other pages were not working. I did some testing and found out that my problem was that PHP4 was now running not PHP5. The pages that I developed use PHP5. I am assuming that when I install the package libphp-phpmailer that is reverted Apache2 to use PHP4. I need some help to get apache2 working with PHP5 I tried installing php5 but that does not seam to work, apt-get says that php5 is already installed. I am a little stumped on how to change apache2 to load php5 not php4 I am not concerned about the PHP Mailer working. I would like to get it all working together but I need PHP5 working more then I need the PHP Mailer functions working.

If anyone can help me out I would greatly appreciate it.:)

---

### Post by ryjal on 2007-12-14
Ok I figured out the problem when I installed the libphp-phpmailer package apt-get installes php4 and uninstalls libapache2-mod-php5 so what I did was save the files installed from the libphp-phpmailer package located in the libphp-phpmailer folder. then I installed the libapache2-mod-php5 package and then apt-get uninstalls the libphp-phpmailer package and the  libapache2-mod-php4 package. PHP5 now is loaded by apache2 and my php pages work. To use the phpmailer class I just pointed my php file to where I had saved the libphp-phpmailer files and php mailer works just fine.:)

---

