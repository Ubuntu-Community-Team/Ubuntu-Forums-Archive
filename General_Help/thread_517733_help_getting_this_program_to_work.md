---
title: "help getting this program to work?"
date: 2007-08-04
forum: General Help
---

### Post by cessna_89702 on 2007-08-04
[http://linux.softpedia.com/get/Programming/Libraries/WWW-Myspace-FriendAdder-29246.shtml](http://linux.softpedia.com/get/Programming/Libraries/WWW-Myspace-FriendAdder-29246.shtml)


you need to download it to get the readme. 

thanks

---

### Post by be4truth on 2007-08-04
Why don't you post the readme as an attachment?

---

### Post by cessna_89702 on 2007-08-04
WWW-Myspace-FriendAdder

This module has been split off from the WWW::Myspace distribution.  This was
done in order to provide a more lightweight WWW::Myspace distro, while
allowing folks who need more options to install WWW::Myspace::FriendAdder in
addition to WWW::Myspace.  

INSTALLATION

To install this module, run the following commands:

    perl Makefile.PL
    make
    make test
    make install


SUPPORT AND DOCUMENTATION

After installing, you can find documentation for this module with the perldoc 
command.

    perldoc WWW::Myspace::FriendAdder

You can also look for information at:

    Search CPAN
        [http://search.cpan.org/dist/WWW-Myspace-FriendAdder](http://search.cpan.org/dist/WWW-Myspace-FriendAdder)

    CPAN Request Tracker:
        [http://rt.cpan.org/NoAuth/Bugs.html?Dist=WWW-Myspace-FriendAdder](http://rt.cpan.org/NoAuth/Bugs.html?Dist=WWW-Myspace-FriendAdder)

    AnnoCPAN, annotated CPAN documentation:
        [http://annocpan.org/dist/WWW-Myspace-FriendAdder](http://annocpan.org/dist/WWW-Myspace-FriendAdder)

    CPAN Ratings:
        [http://cpanratings.perl.org/d/WWW-Myspace-FriendAdder](http://cpanratings.perl.org/d/WWW-Myspace-FriendAdder)

COPYRIGHT AND LICENCE

Copyright (C) 2006 - 2007 Olaf Alders

This program is free software; you can redistribute it and/or modify it
under the same terms as Perl itself.
















im not sure how to run it

---

### Post by nitro_n2o on 2007-08-05
let's say the file is saved on desktop 
open a terminal 
and copy & paste OR preferably type the following
```
tar -xvzf Desktop/WWW-Myspace-FriendAdder.tar.gz
perl Makefile.PL
make
make test
sudo make install
```
and done! :)

---

### Post by be4truth on 2007-08-05
Don't you have to cd into the folder before you run perl and the rest?

---

### Post by nitro_n2o on 2007-08-05
> **be4truth said:**
> Don't you have to cd into the folder before you run perl and the rest?

oop's u r right :oops: shame on me, sorry for that.. you have to do this 
```
tar -xvzf Desktop/WWW-Myspace-FriendAdder.tar.gz
cd Desktop/WWW-Myspace-FriendAdder
perl Makefile.PL
make
make test
sudo make install
```
:)

---

### Post by cessna_89702 on 2007-08-05
ok I have that done but I still dont know how to run it

---

