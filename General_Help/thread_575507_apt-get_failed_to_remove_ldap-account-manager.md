---
title: "apt-get failed to remove ldap-account-manager"
date: 2007-10-14
forum: General Help
---

### Post by AboSamoor on 2007-10-14
accidentally i found that ldap-account-manager package have to be removed, the problem that removing this package require the restarting of apache2 , which returns errors , so apt-get can't proceed and i can't make any upgrades :(.
i don't have to remove that package , but the problem that i can't unmark from synaptic.
i'm not using apache2 .
so if i can remove that package from the remove list for apt-get, it's OK.
if i can configure apache2 to restart without errors, also it's OK.
if i can make the upgrades and installation with that package problem is remaining , OK,
my target is to make upgrades and installations ...
this is the message error 

[http://paste.ubuntu-nl.org/40604/](http://paste.ubuntu-nl.org/40604/)

Removing ldap-account-manager ...
 * Restarting apache 1.3 web server...                                                                     [ OK ] 
 * Restarting web server apache2                                                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.64 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.64 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:80
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                                                           [fail]
invoke-rc.d: initscript apache2, action "restart" failed.
dpkg: error processing ldap-account-manager (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ldap-account-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by por100pre1 on 2007-10-14
Try this:

```
sudo dpkg --configure -a
```

EDIT: Try this too:

```
sudo nano -w /etc/apache2/ports.conf
```

try changing the port apache2 uses just for a while. Then try removing ldap-account-manager again.

---

