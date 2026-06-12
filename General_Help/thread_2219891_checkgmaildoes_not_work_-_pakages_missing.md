---
title: "checkgmaildoes not work - pakages ?missing?"
date: 2014-04-25
forum: General Help
---

### Post by Martin_Wagner on 2014-04-25
Hi, checkgmail stopped working. 
I'm running KDE Mint 16 on an Acer Extensa when I try to start checkgmail # version 1.12.1svn (25/6/2007)

the following code comes up: 
Simple, gtk2::sexy is installed...

```
capponz@extensy:~ > checkgmail
Warning: Crypt::Simple not found ...

CheckGmail requires the above packages for password encryption
Please download and install from CPAN (http://search.cpan.org) if you want to use this feature ...

Warning: Gtk2::Sexy not found ...

CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN (http://search.cpan.org) if you want to use this feature ...

Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.


```

The login dialog appears, but after entering the password, the dialogbox disappears,
But 'simple' is installed, also 'Gtk2::Sexy':

```

capponz@extensy:~ > sudo perl -MCPAN -e 'install XML::Simple'
Going to read '/home/capponz/.cpan/Metadata'
  Database was generated on Thu, 24 Apr 2014 23:17:02 GMT
XML::Simple is up to date (2.20).

capponz@extensy:~ > sudo apt-get install libsexy-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsexy-dev is already the newest version.
The following packages were automatically installed and are no longer required:
   libcrypt-blowfish-perl libfreezethaw-perl libgtk2-trayicon-perl  libmowgli2 libxml-libxml-perl libxml-namespacesupport-perl  libxml-sax-base-perl libxml-sax-perl
  libxml-simple-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

libssl-dev, openssl(i think a system update was the reason for checkgmail to stop working) and SSLeay is up to date:  

```
 capponz@extensy:~ > sudo perl -MCPAN -e 'install Crypt::SSLeay'
Going to read '/home/capponz/.cpan/Metadata'
  Database was generated on Thu, 24 Apr 2014 23:17:02 GMT
Crypt::SSLeay is up to date (0.72).

capponz@extensy:~ > sudo apt-get install libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libssl-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libcrypt-blowfish-perl libfreezethaw-perl libgtk2-trayicon-perl libmowgli2 libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-base-perl libxml-sax-perl
  libxml-simple-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

capponz@extensy:~ > sudo apt-get install openssl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
The following packages were automatically installed and are no longer required:
  libcrypt-blowfish-perl libfreezethaw-perl libgtk2-trayicon-perl libmowgli2 libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-base-perl libxml-sax-perl
  libxml-simple-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

Could someone please point me into right direction?
thanks a lot!

---

