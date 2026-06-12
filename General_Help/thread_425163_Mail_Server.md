---
title: "Mail Server"
date: 2007-04-27
forum: General Help
---

### Post by helios12 on 2007-04-27
Hi all,

I am new to the forums, so if this is posted in the wrong section, my apologies.

I am hosted on a windows server, but am having issues with their mail setup. Most emails being received just bounce due to the VERY strict spam filter.

I have therefore decided to setup my own mail server on one of my linux boxes at home. Now on the DNS editor on my helm i have the following option: mail.mydomain.com.[21] for the mx entry. And the relevant a records exist. Now i would need to change this to my IP, but how would i go about setting up the mail server on my ubuntu linux, so it would recognise the email for that domain. I am pretty new to this so could someone point me in the direction of a tutorial etc.

Thanks,

---

### Post by darrenm on 2007-04-27
```
sudo apt-get install postfix
```

Then just answer the questions.

Then edit /etc/postfix/main.cf and change at least myorigin , mydomain , myhostname and mydestination

All very simple. You could also try the MySQL Postfix howto if you're feeling like getting your hands dirty. [http://ubuntuforums.org/showthread.php?t=398866](http://ubuntuforums.org/showthread.php?t=398866)

---

### Post by helios12 on 2007-04-27
thanks for that, anyone got any other tutorials before i goahead with this Ruby on Rails setup.

---

