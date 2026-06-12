---
title: "Ubuntu 14.04 CPAN / HACI"
date: 2018-04-05
forum: General Help
---

### Post by edunnington on 2018-04-05
Hello,

I am attempting to install HaCi ([http://haci.larsux.de/wiki/HaCiInstall](http://haci.larsux.de/wiki/HaCiInstall)) on my server. I am trying to get CGI and all of the PERL mods installed on the server but i keep having errors in CPAN.

Can someone please help?

```

cpan[10]> install CGI::Ajax
Running install for module 'CGI::Ajax'
Running make for B/BP/BPEDERSE/CGI-Ajax-0.707.tar.gz
Checksum for /home/evan/.cpan/sources/authors/id/B/BP/BPEDERSE/CGI-Ajax-0.707.tar.gz ok


  CPAN.pm: Building B/BP/BPEDERSE/CGI-Ajax-0.707.tar.gz


Checking if your kit is complete...
Looks good
Writing Makefile for CGI::Ajax
Writing MYMETA.yml and MYMETA.json
Can't exec "make": No such file or directory at /usr/share/perl/5.18/CPAN/Distribution.pm line 2084.
  BPEDERSE/CGI-Ajax-0.707.tar.gz
  make -- NOT OK
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Failed during this command:
 BPEDERSE/CGI-Ajax-0.707.tar.gz               : make NO

```

```

cpan[12]> install Math::BigInt v1.87
Warning: Cannot install v1.87, don't know what it is.
Try the command


    i /v1.87/


to find objects with matching identifiers.
Running install for module 'Math::BigInt'
Running make for P/PJ/PJACKLAM/Math-BigInt-1.999811.tar.gz
Checksum for /home/evan/.cpan/sources/authors/id/P/PJ/PJACKLAM/Math-BigInt-1.999811.tar.gz ok


  CPAN.pm: Building P/PJ/PJACKLAM/Math-BigInt-1.999811.tar.gz


##########################################################################
#
# Some of the new methods will not work unless the following installed
# modules are updated. It is therefore recommended that the modules listed
# below are upgraded after installing this distribution.
#
# Module                         Recommended    Installed
# ------                         -----------    ---------
# Math::BigInt::FastCalc         0.5000         0.30
# Math::BigInt::Calc             1.999800       1.997
#
##########################################################################


Sleeping for a few seconds ...
Checking if your kit is complete...
Looks good
Writing Makefile for Math::BigInt
Writing MYMETA.yml and MYMETA.json
Can't exec "make": No such file or directory at /usr/share/perl/5.18/CPAN/Distribution.pm line 2084.
  PJACKLAM/Math-BigInt-1.999811.tar.gz
  make -- NOT OK
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Failed during this command:
 PJACKLAM/Math-BigInt-1.999811.tar.gz         : make NO

```

I am not a huge Ubuntu expert or know a whole lot about it but i am trying to learn while also getting this software to work.

Thanks for any help.

---

### Post by TheFu on 2018-04-05
I'd use **perlbrew** to keep the system perl and a perl needed for a specific application separate.  Then, from inside the perlbrew environment, you can use cpan as normal without impacting the system perl or system libraries.

Basically, if you use the system installed perl, then you should also only use repository-provided (APT) perl packages.

---

