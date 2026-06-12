---
title: "Dapper: No Apache Binaries or Startup Scripts?"
date: 2007-05-22
forum: General Help
---

### Post by jonwatson on 2007-05-22
Hi All,

I'm having a rather unique problem that I haven't seen before and can't sort out.

I am attempting to install Apache2 onto an existing Dapper server. Running apt-get install apache2 or aptitude install apache2, the install seems to go as planned:
> 
root@server:~# apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/35.8kB of archives.
After unpacking, 81.9kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 61265 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu2.1_i386.deb) ...
Setting up apache2 (2.0.55-4ubuntu2.1) ...
root@server:~# 


Yet there are no apache binaries or startup scripts to be found anywhere:
> 
root@server:~# ls /etc/init.d/apache*
ls: /etc/init.d/apache*: No such file or directory

root@server:~# ls /etc/init.d/http*
ls: /etc/init.d/http*: No such file or directory

root@server:~# which apache
root@server:~# which apache2
root@server:~# which httpd



I've tried uninstalling, reinstalling, and dpkg --purge'ing, but I get the same results. I have apt-get updated and all my repos are uncommented.

Anyhow have any ideas what's going on?

Thanks!

---

### Post by fanatik on 2007-05-22
looks like you need to install apache2-common... the apache2 package doesn't contain very much!

Regards,
James.

---

### Post by Soybean on 2007-05-22
But shouldn't apache2 have apache2-common as a dependency? What makes aptitude miss dependencies like that?

---

### Post by fanatik on 2007-05-22
in fact the package info for apache2-common states:

> This package contains all the standard apache2 modules, including SSL support.
 However, it does *not* include the server itself; for this you need to install
 one of the apache2-mpm-* packages; such as worker or prefork.

So you'd need another package too, so if you install this one: apache2-mpm-prefork it will install apache2-common.

I don't know why apache 2 didn't do that in the 1st place!

---

### Post by jonwatson on 2007-05-22
Thanks for the help,

I had to install the apache2-mpm-prefork to get the binary /usr/sbin/apache2, but I still have no start up scripts. I also had to create the /var/run/apache2 directory in order for the daemon to launch.

I guess I can make a startup script, but I'd prefer the stock one. Any ideas why I don't seem to have them?

Thanks!

---

### Post by mepapp on 2007-05-28
I've got the same problem. If I install apache2.2-common, the /etc/apache2/mods-available folder isn't populated, I have no apache.conf, and no /etc/init.d/apache2. Installing apache2-mpm-prefork seems to provide the binary, but it won't run w/o a config file.

---

