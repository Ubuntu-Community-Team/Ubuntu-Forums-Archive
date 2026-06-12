---
title: "phpmyadmin and blowfish problem"
date: 2006-10-21
forum: General Help
---

### Post by harty83 on 2006-10-21
I installed phpmyadmin a while back and have been using it fine.  Now when I go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) I get an error that says that the config file must have a blowfish_secret.  I checked through the installed config.inc.php and it includes the blowfish_secret.inc.php from /etc/phpmyadmin.  What's the deal?  Thanks ahead of time!

Yes, the blowfish_secret file does include a string of letters and numbers.

---

### Post by az on 2006-10-21
Does this help?

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031-4](https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031-4)

---

### Post by harty83 on 2006-10-21
I'm afraid that didn't work.  I ended up changing the way you log in from cookie to config and manually set up a username/password.

---

### Post by jmrasor on 2007-01-26
Hi All,

  I ran into this problem today on an Edgy workstation with apache2, mysql, php5, all installed with the normal apt-get operations. Installation of phpmyadmin with apt-get completed as well. Apache, mysqladmin, mysql, php5 are all running.

  On surfing to myworkstation/phpmyadmin, I got the "needs blowfish secret" gripe like harty83 did, and found /etc/phpmyadmin/blowfish_secret.inc.php to contain a secret. :(  On doing ls -l in that directory, I saw that the secret, and the htpasswd.setup, have permissions 640, while config.header.inc.php and config.footer.inc.php have 644. 

  I then chmodded the secret to 644 and phpmyadmin presented the normal login screen, and worked.

  HTH.

---

### Post by stuarttaylor on 2007-05-04
I've been having problems staying logged into phpmyadmin on a fresh install of Feisty Fawn 64bit.

I have been able to log in eventually, only to be spat back out again. Having set the authentication type to 'cookie', I realised there must be a problem with the scripts setting and retaining the cookie.

Anyway to cut a long frustrating story short, I was trawling the phpmyadmin forum this morning and found this page [http://sourceforge.net/forum/message.php?msg_id=4288892](http://sourceforge.net/forum/message.php?msg_id=4288892) which talks about a bug where mcrypt isn't installed.

So one 'sudo apt-get install php5-mcrypt' later and it's all sorted now. :-D:-D:-D

---

### Post by viniosity on 2007-05-11
> **jmrasor said:**
> Hi All,

  I then chmodded the secret to 644 and phpmyadmin presented the normal login screen, and worked.

  HTH.

Oh wow.. that's exactly the problem I had.  Thanks for saving me much hair pulling!

---

### Post by CaptainMorgan on 2007-08-19
> **viniosity said:**
> Oh wow.. that's exactly the problem I had.  Thanks for saving me much hair pulling!


Same here, thanks a million.
-Capt

---

