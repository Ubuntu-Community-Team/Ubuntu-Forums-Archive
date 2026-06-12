---
title: "Installing WWW::WebKit - Package gdk-3.0 was not found"
date: 2013-02-25
forum: General Help
---

### Post by brdohman on 2013-02-25
I'm trying to install [WWW::WebKit]("https://metacpan.org/module/WWW::WebKit") with cpan, but keep running up a dependency I can't find information on. 

Here is what I'm running > 


```
cpan[1]> install WWW::WebKit
Reading '/home/user/.cpan/Metadata'
  Database was generated on Sun, 24 Feb 2013 20:29:02 GMT
Running install for module 'WWW::WebKit'
Running make for N/NI/NINE/WWW-WebKit-0.05.tar.gz
Checksum for /home/user/.cpan/sources/authors/id/N/NI/NINE/WWW-WebKit-0.05.tar.gz ok
Scanning cache /home/user/.cpan/build for sizes
.......................................................---------------------DONE
DEL(1/2): /home/user/.cpan/build/Gtk2-1.247-fNyZMQ 
DEL(2/2): /home/user/.cpan/build/CPAN-DistnameInfo-0.12-2hUvRr 

  CPAN.pm: Building N/NI/NINE/WWW-WebKit-0.05.tar.gz

Package gdk-3.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-3.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-3.0' found
 at Makefile.PL line 7.
*** can not find package gdk-3.0
*** check that it is properly installed and available in PKG_CONFIG_PATH
 at Makefile.PL line 7.
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
'YAML' not installed, will not store persistent state
  NINE/WWW-WebKit-0.05.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Could not read metadata file. Falling back to other methods to determine prerequisites
Failed during this command:
 NINE/WWW-WebKit-0.05.tar.gz                  : writemakefile NO '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 256
```

---

### Post by leathan7 on 2013-11-12
I believe this type of problem happens alot during compiling (at first). I know that the package names vary based on the language but for this case its "lib" "dev" you should be searching for...i think.... searching the repositori

For example I did some searches for you and this one may help you
    
apt-cache search libgtk-3.*

    sudo apt-get install libgtk-3-dev
 
might be all you need to do. but this is a general problem ^^

> **brdohman said:**
> I'm trying to install [WWW::WebKit]("https://metacpan.org/module/WWW::WebKit") with cpan, but keep running up a dependency I can't find information on. 

Here is what I'm running > 


```
cpan[1]> install WWW::WebKit
Reading '/home/user/.cpan/Metadata'
  Database was generated on Sun, 24 Feb 2013 20:29:02 GMT
Running install for module 'WWW::WebKit'
Running make for N/NI/NINE/WWW-WebKit-0.05.tar.gz
Checksum for /home/user/.cpan/sources/authors/id/N/NI/NINE/WWW-WebKit-0.05.tar.gz ok
Scanning cache /home/user/.cpan/build for sizes
.......................................................---------------------DONE
DEL(1/2): /home/user/.cpan/build/Gtk2-1.247-fNyZMQ 
DEL(2/2): /home/user/.cpan/build/CPAN-DistnameInfo-0.12-2hUvRr 

  CPAN.pm: Building N/NI/NINE/WWW-WebKit-0.05.tar.gz

Package gdk-3.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-3.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-3.0' found
 at Makefile.PL line 7.
*** can not find package gdk-3.0
*** check that it is properly installed and available in PKG_CONFIG_PATH
 at Makefile.PL line 7.
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
'YAML' not installed, will not store persistent state
  NINE/WWW-WebKit-0.05.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Could not read metadata file. Falling back to other methods to determine prerequisites
Failed during this command:
 NINE/WWW-WebKit-0.05.tar.gz                  : writemakefile NO '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 256
```

---

