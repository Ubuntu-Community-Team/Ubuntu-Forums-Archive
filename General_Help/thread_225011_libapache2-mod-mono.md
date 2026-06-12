---
title: "libapache2-mod-mono"
date: 2006-07-28
forum: General Help
---

### Post by SigmaX on 2006-07-28
Trying to install mod_mono for Apache2 on Dapper.

```
$ sudo apt-get install libapache2-mod-mono
```

Installed fine.  

```
$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... apache2: could not open document config file /etc/mono-server/mono-server-hosts.conf
                                                                         [fail]

```

Appears to be a path issue...

```
$ sudo ln -s /etc/mono-server2 /etc/mono-server
$ sudo ln -s /etc/mono-server2/mono-server2-hosts.conf /etc/mono-server2/mono-server-hosts.conf
$ sudo /etc/init.d/apache2 reload  * Reloading apache 2.0 configuration... httpd not running, trying to start
                                                                         [ ok ]

```

Looks good...  Except when I actually try to access a .aspx page in Firefox, it doesn't process it and display it, instead offering to let me download the .aspx file.

Any help?  Is the libapache2-mod-mono package broken like that, or have I got something wrong from ground zero?

SigmaX

---

### Post by Jabran Asghar on 2006-11-08
Hi,

Could you find a solution? I am also stcuk at this on a new server.

Thanks for any feedback.

Jabran

---

