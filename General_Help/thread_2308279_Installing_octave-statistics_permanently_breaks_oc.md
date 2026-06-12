---
title: "Installing octave-statistics permanently breaks octave in 14.04"
date: 2016-01-01
forum: General Help
---

### Post by timothylegg on 2016-01-01
I have been using octave for ages on my 14.04 installation.  But I needed a normal probability plot, so I installed octave-statistics and that broke octave.

> ~$ octave
GNU Octave, version 3.8.1
Copyright (C) 2014 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type 'warranty'.


Octave was configured for "x86_64-pc-linux-gnu".


Additional information about Octave is available at [http://www.octave.org](http://www.octave.org).


Please contribute if you find this software useful.
For more information, visit [http://www.octave.org/get-involved.html](http://www.octave.org/get-involved.html)


Read [http://www.octave.org/bugs.html](http://www.octave.org/bugs.html) to learn how to submit bug reports.
For information about changes from previous versions, type 'news'.


error: javaMethod: /usr/lib/jvm/default-java/jre/lib/amd64/server/libjvm.so: failed to load: /usr/lib/jvm/default-java/jre/lib/amd64/server/libjvm.so: cannot open shared object file: No such file or directory
error: called from:
error:   /usr/share/octave/3.8.1/m/java/javaaddpath.m at line 51, column 13
error:   /usr/share/octave/packages/io-2.0.2/PKG_ADD at line 31, column 7
error: addpath: all arguments must be character strings
error:   /usr/share/octave/3.8.1/m/pkg/private/load_packages_and_dependencies.m at line 47, column 5
error:   /usr/share/octave/3.8.1/m/pkg/private/load_packages.m at line 60, column 3
error:   /usr/share/octave/3.8.1/m/pkg/pkg.m at line 412, column 7
error:   /usr/share/octave/3.8.1/m/startup/octaverc at line 22, column 1


But even worse, I did apt-get remove octave-statistics, and it even broke that:

> Removing octave-statistics (1.2.3-1) ...
Processing triggers for octave (3.8.1-1ubuntu1) ...
error: javaMethod: /usr/lib/jvm/default-java/jre/lib/amd64/server/libjvm.so: failed to load: /usr/lib/jvm/default-java/jre/lib/amd64/server/libjvm.so: cannot open shared object file: No such file or directory
error: called from:
error:   /usr/share/octave/3.8.1/m/java/javaaddpath.m at line 51, column 13
error:   /usr/share/octave/packages/io-2.0.2/PKG_ADD at line 31, column 7
error: addpath: all arguments must be character strings
error:   /usr/share/octave/3.8.1/m/pkg/private/load_packages_and_dependencies.m at line 47, column 5
error:   /usr/share/octave/3.8.1/m/pkg/private/load_packages.m at line 60, column 3
error:   /usr/share/octave/3.8.1/m/pkg/pkg.m at line 412, column 7
error:   /usr/share/octave/3.8.1/m/startup/octaverc at line 22, column 1
dpkg: error processing package octave (--remove):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 octave
E: Sub-process /usr/bin/dpkg returned an error code (1)



I'd love to have octave back again without reinstalling.


Now for the rest of this messages is a flaming rant about this even happening in the first place.

I'm also curious how a defective/malicious package can:
 * pass Ubuntu standards to be allowed to exist in the first place
 * be uninstallable by breaking apt-get's scripts

To me, this is quite unacceptable.  I have a spare computer I can run octave on, but this was my prized virtual machine that was my primary swiss-army-knife-can-do-anything-real-work environment that I typically shelter from unnecessary or unofficial software.  So somebody is able to create an official ubuntu package that breaks a different package and defeats the uninstaller.  That is precisely the main reason I left windows, because that is malware by my definition.

---

### Post by steeldriver on 2016-01-01
I wonder if it's a java version compatibility issue? What version(s) of java do you have installed?

It's a bit of a leap to start talking about packages being "defective/malicious" imho

---

