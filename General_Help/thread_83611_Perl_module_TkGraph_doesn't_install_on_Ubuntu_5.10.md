---
title: "Perl module Tk::Graph doesn't install on Ubuntu 5.10"
date: 2005-10-29
forum: General Help
---

### Post by hollie on 2005-10-29
Hello,

I'm trying to get MaPiVi, a picture viewer, running on Breezy Badger (fully updated). This program is Perl-based and depends on certain Perl modules.

I'm used to running Perl on Linux systems (RedHat, Fedora, Gentoo) and normally I use the CPAN module to install extra Perl modules.

However, I read that on Ubuntu it is the idea to also use the Synaptic package manager to install extra packages for Perl.

Depending on information I found in [another thread]("http://ubuntuforums.org/showthread.php?t=6054") on this forum, I already installed the packages:
[INDENT][LIST]
[*]libtk-img (version 1:1.3-13)
[*]libimage-info-perl (version 1.16-2)
[/LIST][/INDENT]

The package 'Tk' is also already installed (perl-tk v 1:800.025-2).

However, if I run
```
perl -e "use Tk::JPEG;"
```

I still get the error:
```
Can't locate Tk/JPEG.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at -e line 1.
BEGIN failed--compilation aborted at -e line 1.
```

Which indicates that the package is not installed correctly.

If I try to install the package 'the usual way' with
```
sudo perl -MCPAN -e shell
cpan> install Tk::JPEG

```

it also fails with:
```
Using -L/usr/lib to find /usr/lib/libX11.so.6.2.0
Cannot find X include files via /usr/include
Cannot find X include files anywhere at ./myConfig line 332.
Compilation failed in require at Makefile.PL line 36.
```

Can someone please shed some light on this?

Thanks,
 Lieven.

---

### Post by Boss Happy on 2006-01-21
Hi,
I'm a newbie and I've also been trying to install the Tk::JPEG module for perl.  I had the same error.  I got one step closer by installing "libx11-dev" through synaptic or apt-get

*sudo apt-get install libx11-dev*

FYI:  I did this then tried to install the Tk::JPEG module and it still failed.  It won't pass the *make test* part.  I hope you have better luck.

---

### Post by JeffreyRatcliffe on 2006-01-28
Did you manage to get MaPiVi working? If so, how?

It would be nice if there were a .deb for it.

Regards

Jeff

---

### Post by philxxx on 2006-02-13
Before I start to spent time to install MaPiVi I would like to know if someone has done it before!

Best regards from berlin / germany

p hil

---

### Post by Martin-Herrmann on 2006-05-02
Hi,

yes, Mapivi works on my Ubuntu 5.10.
I had to install the newest version of Perl/Tk ([http://search.cpan.org/~ni-s/Tk-804.027/]("http://search.cpan.org/~ni-s/Tk-804.027/")). 
This version includes Tk::JPEG.
Following these steps: unzip, unpack, perl Makefile.PL, make, make test, sudo make install.
I had to install several other packages using apt-get (cc, gcc, X11-Include files etc.) on my Ubuntu v5.10 first.
Please drop me an email if you need further assistance.

Regards,
  Martin - Author of Mapivi

---

