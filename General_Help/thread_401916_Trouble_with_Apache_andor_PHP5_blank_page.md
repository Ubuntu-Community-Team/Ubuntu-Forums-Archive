---
title: "Trouble with Apache and/or PHP5: blank page"
date: 2007-04-05
forum: General Help
---

### Post by jrohde on 2007-04-05
Hi,

I have a fresh Ubuntu Edgy 32bit desktop on which I have installed Apache2, MySQL, PHP5, GD etc. according to the instructions found on Ubuntuguide.org. Everything went ok.

There is a problem though. I am trying to install Typo3, but all I get when I access [http://localhost](http://localhost) is an empty page - no source code at all. It should show the installation wizard of Typo3. 

I have tried creating a test file called phpinfo.php and it works ok, so PHP isn't the problem. I have chmod'ed /var/www/* til www-data:www-data, and this didn't change anything.

So I'm out of ideas. Any suggestions?

Thanks,

Jakob

---

### Post by Paul41 on 2007-04-05
It sounds like there is some kind of error in the Typo3 page.  The default setup is for errors not to display to the screen for security reasons, so if there is a error you frequently get a blank page. Check your Apache error log to see if there is anything there. I am away from my Ubuntu computer right now and I can't remember exactly where the log file is. If you can't find it and no one else posts it I will let you know where it is later today.

---

### Post by raptor2552 on 2007-04-05
Look here if you haven't customized Apache too much: /var/log/apache2/error.log

---

### Post by bnoyes on 2007-04-23
Just wanted to jump in here too. I have been hosting Wordpress MU on my apache2 php5 mysql5 setup for quite a while now with no issues. I just upgraded to Feisty Fawn and I am now having the same blank page issue. My apache2.2 log is clean. Anybody know what has changed in this last upgrade?

Update:

After some serious research here in the forums, removing and reinstalling the LAMP components I found a plugin within my WordpressMU installation that was causing the blank pages. I can't figure out why the plugin caused the blank page problem ONLY after upgrading to Feisty Fawn. Seems some PHP code is not liked by the upgraded versions of LAMP in Feisty.

---

### Post by depi on 2007-04-28
I have the same issue with my PHP pages, any other ideas?

---

