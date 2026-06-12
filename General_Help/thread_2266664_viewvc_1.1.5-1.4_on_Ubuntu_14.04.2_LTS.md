---
title: "viewvc 1.1.5-1.4 on Ubuntu 14.04.2 LTS"
date: 2015-02-24
forum: General Help
---

### Post by Habitual on 2015-02-24
Well, I managed to get it working on a Virtualbox running debian 7.8 Wheezy.
But I'll be damned if I can replicate the steps to an Ubuntu 14.04.2 LTS server.

[http://ubuntuhost.com/viewvc](http://ubuntuhost.com/viewvc) just shows me python code.

Debian host:
Server version: Apache/2.2.22 (Debian)

Ubuntu host:
Server version: Apache/2.4.7 (Ubuntu)

both installed using ```
apt-get install viewvc
``` and both are viewvc 1.1.5-1.4

I can manage to run the stand-alone server using ```
/usr/lib/viewvc/bin/standalone.py -r /var/www/svn/cirrhus9/ -d
```
and navigate to it using ```
lynx http://localhost:49152/viewvc
``` and see what I expect to see on the Ubuntu host.

but using Firefox or Chrome just shows me python code.

I read carefully this [INSTALL]("http://viewvc.tigris.org/source/browse/*checkout*/viewvc/trunk/INSTALL") (from trunk) even though I am not installing from trunk.

The /etc/apache2/apache2.conf on the debian host  only needed 1 line to work:
```
### Viewvc
ScriptAlias /viewvc /usr/lib/viewvc/cgi-bin/viewvc.cgi
```

The same line on the Ubuntu host just shows me python code.

I'd appreciate any help you may offer.
Thanks for your time.

---

