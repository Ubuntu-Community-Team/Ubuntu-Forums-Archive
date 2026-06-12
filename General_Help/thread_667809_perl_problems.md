---
title: "perl problems"
date: 2008-01-14
forum: General Help
---

### Post by decadude on 2008-01-14
# perl
/usr/bin/perl: line 15: use: command not found
/usr/bin/perl: line 17: =10.10.10.114: command not found
/usr/bin/perl: line 18: =80: command not found
/usr/bin/perl: line 19: syntax error near unexpected token `('
/usr/bin/perl: line 19: `$sock = IO::Socket::INET->new(PeerAddr => $host,PeerPort => $port, Proto => 'tcp') || die "new error$@\n";'


it also has seemed to mess up apt-get

# apt-get install nikto
Reading package lists... Done
Building dependency tree
Reading state information... Done
nikto is already the newest version.
The following packages were automatically installed and are no longer required:
  snort-rules-default libcompizconfig0 module-assistant libdecoration0
  libcompizconfig-backend-gconf compiz-plugins libusb-dev libtifiles0-dev
  compiz-fusion-plugins-extra html2text compiz libprelude2 compiz-core
  compiz-fusion-plugins-main snort-common-libraries compiz-gnome
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
/usr/sbin/dpkg-preconfigure: 6: BEGIN: not found
eval: 1: qq{: not found
/usr/sbin/dpkg-preconfigure: 8: use: not found
/usr/sbin/dpkg-preconfigure: 9: use: not found
/usr/sbin/dpkg-preconfigure: 10: Syntax error: "(" unexpected
Setting up perl (5.8.8-7ubuntu3.1) ...
/bin/sh: Can't open update-alternatives
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 2
Setting up cupsys (1.3.2-1ubuntu7.3) ...
/usr/share/debconf/frontend: 5: use: not found
/usr/share/debconf/frontend: 6: use: not found
/usr/share/debconf/frontend: 7: use: not found
/usr/share/debconf/frontend: 8: Syntax error: "(" unexpected
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 perl
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)


anything i try to apt-get install is messed up

my problem originated from trying to get crossover office to run correctly on my system, those guys told me there was an evident problem with my perl so i went into synaptics and tried the reinstall option and no luck there either.

---

