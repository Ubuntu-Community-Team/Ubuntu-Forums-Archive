---
title: "package is missing, has been obsoleted, or is only available from another source"
date: 2016-08-12
forum: General Help
---

### Post by EnderUSAF on 2016-08-12
Hello,

I have a libreNMS server that I made the mistake of trying to upgrade to 16.04.  After upgrading I ran into some problems due to 16.04 using php7 while LibreNMS was calling for php5.  I installed the PPA so I can install php5 and at least the website portion of LibreNMS now works, though the polling does not.  I spoke with the guys at LibreNMS and they had me run a validate command and said I was missing items from the install and asked me to run the following command.


apt-get install libapache2-mod-php5 php5-cli php5-mysql php5-gd php5-snmp php-pear php5-curl snmp graphviz php5-mcrypt php5-json apache2 fping imagemagick whois mtr-tiny nmap python-mysqldb snmpd php-net-ipv4 php-net-ipv6 rrdtool git

Found on:  [http://docs.librenms.org/Installation/Installation-(Debian-Ubuntu)/](http://docs.librenms.org/Installation/Installation-(Debian-Ubuntu)/)

When I do I get some missing packages  that show no installation candidate.  Here's the output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libapache2-mod-php5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package php5-cli is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  php7.0-cli:i386 php7.0-cli

Package php5-mcrypt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package php5-mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package php5-gd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libapache2-mod-php5' has no installation candidate
E: Package 'php5-cli' has no installation candidate
E: Package 'php5-mysql' has no installation candidate
E: Package 'php5-gd' has no installation candidate
E: Unable to locate package php5-snmp
E: Unable to locate package php5-curl
E: Package 'php5-mcrypt' has no installation candidate
E: Unable to locate package php5-json


Any ideas on how to get this to work?  Or should I just give up and re-build the server?

php -v
PHP 5.6.24-1+deb.sury.org~xenial+1 (cli)

---

### Post by CatKiller on 2016-08-12
You could potentially grab the old packages from packages.ubuntu.com, or ask the maintainers of the PPA you used to add them, or find a more comprehensive PPA for php5.

---

### Post by #&amp;thj^% on 2016-08-12
See if this is helpful: [http://stackoverflow.com/questions/37197539/an-issue-after-ppaondrej-php5-deprecation](http://stackoverflow.com/questions/37197539/an-issue-after-ppaondrej-php5-deprecation)

---

