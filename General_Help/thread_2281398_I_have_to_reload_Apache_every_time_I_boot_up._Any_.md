---
title: "I have to reload Apache every time I boot up. Any idea why?"
date: 2015-06-06
forum: General Help
---

### Post by Jamison_Bryant on 2015-06-06
Hey guys,

I have a LAMP stack running on Trusty, and in that stack I have a couple of Vhosts configured. Each Vhost is listening on a particular subdomain (of my local network) and everything pretty much works fine there.

BUT, when I cold boot (say when I'm switching OSes), I always have to reload Apache in order for my Vhosts to work. I use this command: ```
sudo service apache2 reload
```.

If I don't run this command and I visit one of my subdomains, I get a directory listing like Apache usually provides.

Anybody have any experience with this issue? It's a minor annoyance at best, but I thought I'd ask.

Regards,

RJ

---

### Post by tgalati4 on 2015-06-06
Look at the apache log files in /var/log.  It could be a timing issue or a preload issue.  You could add a sleep statement to the apache control script so that it loads a couple of minutes after boot.  Or you could add the reload command to /etc/rc.local (without sudo) which is one of the last scripts to get executed after boot.

Welcome to the forums.

---

### Post by SeijiSensei on 2015-06-07
Follow the advice here [http://askubuntu.com/questions/221293/why-is-chkconfig-no-longer-available-in-ubuntu](http://askubuntu.com/questions/221293/why-is-chkconfig-no-longer-available-in-ubuntu) to use sysv-rc-conf.  You'll have to install it first with "sudo apt-get install sysv-rc-conf".  On my testbed server, it returns "on" for run levels 2-5 and "off" for 0, 1, and 6.  This is the proper configuration to start the server at boot.  If that's not what you see, then run "sudo sysv-rc-conf apache2 on".

---

