---
title: "How does perl cpan work with apt-get?"
date: 2021-04-05
forum: General Help
---

### Post by turtles on 2021-04-05
Hello how does Perl CPAN talk with/share data with apt-get in Ubuntu?
For example I need to install a Perl package that depends on say File::Type will CPAN on Ubuntu determine if this package is in a Ubuntu repo first, before downloading from CPAN?
I am getting a make error with cpan and it seems File::Type should be a Ubuntu pacakge
```

Running make for P/PM/PMISON/File-Type-0.22.tar.gz

Can't exec "make": No such file or directory at /usr/share/perl/5.22/CPAN/Distribution.pm line 2243.
```

Thanks

---

### Post by TheFu on 2021-04-06
There is no direct connection between Debian packed Perl modules used by Canonical and MetaCPAN. Canonical (or perhaps Debian) manually maintain them and dependencies.

If just using the system perl, then check for the specific perl modules using **apt search**.  Something like this:
```
$ sudo apt search file-type |grep perl

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libfile-type-perl/focal,focal 0.22-3 all
libfile-type-webimages-perl/focal,focal 1.01-2 all
```

It appears that libfile-type-perl is the package to be installed.
```
sudo apt install libfile-type-perl
```

If you are creating custom Perl, then the best practice is NOT to trust the system version of Perl at all.  Use **Perlbrew** to setup separate perl versions and install metacpan modules into the specific Perl environment.

---

### Post by turtles on 2021-04-08
Wow well thanks for the reply!
and *sigh* thats a bummer, 
from what I understand all the packages in CPAN are not automagically in Ubuntu/Debian repositories?
One would think there is some kind of CPAN wrapper for apt-get no?
Like Gentoo's g-cpan, to manage Perl dependencies.

[I needed to install ODF::lpOD]("https://ubuntuforums.org/showthread.php?t=2460156") on a server and there is no Ubuntu package for it.
So I used CPAN, the first glitch in CPAN is build-essential is not a dependency so its seems broken right out of the gate.
got build-essential installed, 
However CPAN wants to install File::Type A dependency of ODF::lpOD via CPAN.
However there is an Ubuntu package for that:
libfile-type-perl
Now when I go to update my outdated Ubuntu system to a new version of Perl, will it know about all the perl stuff installed via CPAN?
Many thanks and stay safe.
--Turtle

---

### Post by TheFu on 2021-04-08
> **turtles said:**
>  
from what I understand all the packages in CPAN are not automagically in Ubuntu/Debian repositories?
I wouldn't know. 
First, CPAN is dead.  metacpan has been the perl packaging system for some time.  
Second, metacpan has changes daily. It would be ludicrous for a stable release like Ubuntu to have to test all those changes.  
**New is the enemy of stable.**

> **turtles said:**
>  One would think there is some kind of CPAN wrapper for apt-get no?
I wouldn't know.

> **turtles said:**
> Like Gentoo's g-cpan, to manage Perl dependencies.
I wouldn't know.  I don't consider gentoo ready for production use across millions and millions of systems.  Gentoo is for people who need total control over what is installed.  That's a very different mandate than Ubuntu's.

> **turtles said:**
> Now when I go to update my outdated Ubuntu system to a new version of Perl, will it know about all the perl stuff installed via CPAN?
You won't be getting a new version of perl from Canonical. You might get a 4th-level update if any of the packaged perl stuff has some huge security issue in the Canonical packages.  Otherwise, it isn't broken and new is the enemy of stable.

If you need control over the version of perl for your personal programs, use perlbrew and setup a perl environment, access metacpan and load any modules you need that way.  NEVER TOUCH THE SYSTEM PERL.  The system-perl is for use by the system. Lots of scripts used to run Ubuntu as an OS are dependent on the specific way and functionality for that exact version of perl and the pre-packaged perl modules.

BTW, the same statement applies to ruby and python too. Use the pyenv or rbenv/rvm to setup specific versions of those scripting languages if the system versions aren't what you need. Install modules/gems into the environment as needed.  NEVER touch the system Ruby/Python.

You can find where people decided to upgrade the system python and couldn't boot afterwards in these forums.  Don't do it. You've been warned.

---

