---
title: "reinstalling php5 apache2 but /etc/apache2 not reset help please"
date: 2008-03-01
forum: General Help
---

### Post by cyril0 on 2008-03-01
Hello

I have been messing about with apache and php5 and managed to royally mess them up

I wanted to restore them to "factory default" so I did and 

apt-get remove --purge apache php5 phpmyadmin

I then deletd /etc/apache2 and /etc/php5 and tried to 

apt-get install apache2 php5

but after the install the config files in /etc are not there.  How do I force the apt system to install the default config files?  I have a few modules install in my apache configuration but I just want to start fresh with apache2 and php5 and I don't want to reinstall the whole server.

I am running xubuntu gutsy

Please advise

Thanks

---

### Post by David.Vodafone on 2008-03-01
I am having this same issue aswell

---

### Post by David.Vodafone on 2008-03-01
after after doing a purge and an install and a reinstall, i managed to bring back all the conf files, but however my httpd.conf is blank.. is this normal?

---

### Post by Xiong Chiamiov on 2008-04-07
By default the httpd.conf is blank.  All the preset configuration is in apache2.conf.

---

