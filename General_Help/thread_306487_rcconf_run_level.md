---
title: "rcconf run level"
date: 2006-11-25
forum: General Help
---

### Post by wizzkid on 2006-11-25
Hi Guys,

I am currently setting up a test email server and it asked me to arrange the run level of postfix, mysql, apache etc. 

on the quoted texts, is the instruction provided by [http://wiki.archlinux.org/index.php/PostFix_Howto](http://wiki.archlinux.org/index.php/PostFix_Howto)

> 
Step 10. /etc/rc.conf
Add postfix to the list of daemons. Put it near the right side, after iptables and network. Put it after mysqld, as we are going to be using mysql for some of the virtual domain information storage. It is also best to put it before httpd, as it might be possible, however unlikely, for a webmail user to try something before postfix has fully started.

DAEMONS=(syslog-ng hotplug !pcmcia iptables network netfs crond sshd mysqld postfix httpd)


How can I setup the run level of my applications? :)

Thanks

---

### Post by wizzkid on 2006-11-26
any help here?:

---

