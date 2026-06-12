---
title: "Difficulties installing zimbra open source onto 14.04"
date: 2016-01-12
forum: General Help
---

### Post by gabriel64 on 2016-01-12
Hey guys, last night, I was installing zimbra open source onto ubuntu 14.04. I was doing the install, then realized I forgot to set something that was required, so I ctrl-C'd out of the install, fixed it, uninstalled the packages that had been installed (just zimbra-core at that point), and then ran the install again. This time, though, when I run the install, I get this:

sudo ./install.sh


Operations logged to /tmp/install.log.1262
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-dnscache...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-convertd...NOT FOUND
    zimbra-memcached...NOT FOUND
    zimbra-proxy...NOT FOUND
    zimbra-archiving...NOT FOUND
    zimbra-core...FOUND zimbra-core-8.6.0.GA.1153.UBUNTU14.64
ZCS upgrade from 8.6.0 to 8.6.0 will be performed.
Validating ldap configuration
Can't locate Net/LDAP.pm in @INC (you may need to install the Net::LDAP module) (@INC contains: /opt/zimbra/zimbramon/lib /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at bin/zmValidateLdap.pl line 23.
BEGIN failed--compilation aborted at bin/zmValidateLdap.pl line 23.
Error: Unable to bind to the LDAP server as the root LDAP user.
       This is required to upgrade.
[EMAIL="gabriel@gabriel-desktop:~/Desktop/zcs-8.6.0_GA_1153.UBUNTU"]gabriel@gabriel-desktop:~/Desktop/zcs-8.6.0_GA_1153.UBUNTU[/EMAIL]14_64.20141215151116$ sudo ./install.sh -u


Operations logged to /tmp/install.log.1398
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-dnscache...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-convertd...NOT FOUND
    zimbra-memcached...NOT FOUND
    zimbra-proxy...NOT FOUND
    zimbra-archiving...NOT FOUND
    zimbra-core...FOUND zimbra-core-8.6.0.GA.1153.UBUNTU14.64


Saving existing configuration file to /opt/zimbra/.saveconfig


Completely remove existing installation? [N] y


Shutting down zimbra mail


Removing existing packages


   zimbra-core...done


Removing deployed webapp directories


Removing /opt/zimbra
Removing zimbra crontab entry...done.
Cleaning up zimbra init scripts...done.
Cleaning up /etc/ld.so.conf...done.
Cleaning up /etc/security/limits.conf...done.


Finished removing Zimbra Collaboration Server.


[EMAIL="gabriel@gabriel-desktop:~/Desktop/zcs-8.6.0_GA_1153.UBUNTU"]gabriel@gabriel-desktop:~/Desktop/zcs-8.6.0_GA_1153.UBUNTU[/EMAIL]14_64.20141215151116$ sudo ./install.sh


Operations logged to /tmp/install.log.1557
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-dnscache...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-convertd...NOT FOUND
    zimbra-memcached...NOT FOUND
    zimbra-proxy...NOT FOUND
    zimbra-archiving...NOT FOUND
    zimbra-core...FOUND zimbra-core-8.6.0.GA.1153.UBUNTU14.64
ZCS upgrade from 8.6.0 to 8.6.0 will be performed.
Validating ldap configuration
Can't locate Net/LDAP.pm in @INC (you may need to install the Net::LDAP module) (@INC contains: /opt/zimbra/zimbramon/lib /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at bin/zmValidateLdap.pl line 23.
BEGIN failed--compilation aborted at bin/zmValidateLdap.pl line 23.
Error: Unable to bind to the LDAP server as the root LDAP user.
       This is required to upgrade.

So it looks like zimbra core hasn't been installed, so I ran ./install.sh -u, and I get this every time I do:

sudo ./install.sh -u


Operations logged to /tmp/install.log.2450
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-dnscache...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-convertd...NOT FOUND
    zimbra-memcached...NOT FOUND
    zimbra-proxy...NOT FOUND
    zimbra-archiving...NOT FOUND
    zimbra-core...FOUND zimbra-core-8.6.0.GA.1153.UBUNTU14.64


Saving existing configuration file to /opt/zimbra/.saveconfig


Completely remove existing installation? [N] y


Shutting down zimbra mail


Removing existing packages


   zimbra-core...done


Removing deployed webapp directories


Removing /opt/zimbra
Removing zimbra crontab entry...done.
Cleaning up zimbra init scripts...done.
Cleaning up /etc/ld.so.conf...done.
Cleaning up /etc/security/limits.conf...done.


Finished removing Zimbra Collaboration Server.


So, it looks like it either won't uninstall correctly, or it thinks that core is still installed when it isn't......

Any help with this is much appreciated!!



(Also, I'm new to this site, so if this is in the wrong place, sorry!)

---

