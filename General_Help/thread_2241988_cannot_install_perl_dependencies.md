---
title: "cannot install perl dependencies"
date: 2014-08-29
forum: General Help
---

### Post by bobmounger on 2014-08-29
Greetings, 

I am trying to run ecantorix on  a 14.04 laptop. It has perl dependencies & I have tried to install them, it always says the install worked,  but I always get these errors when I try to actually use the module. what am I doing wrong?

$ cpanm install Math::FFT
--> Working on install
Fetching [http://www.cpan.org/authors/id/D/DA/DAGOLDEN/install-0.01.tar.gz](http://www.cpan.org/authors/id/D/DA/DAGOLDEN/install-0.01.tar.gz) ... OK
Configuring install-0.01 ... OK
Building and testing install-0.01 ... OK
Successfully installed install-0.01
--> Working on Math::FFT
Fetching [http://www.cpan.org/authors/id/R/RK/RKOBES/Math-FFT-1.28.tar.gz](http://www.cpan.org/authors/id/R/RK/RKOBES/Math-FFT-1.28.tar.gz) ... OK
Configuring Math-FFT-1.28 ... OK
Building and testing Math-FFT-1.28 ... OK
Successfully installed Math-FFT-1.28
2 distributions installed


$ perl -e 'use Math::FFT;'
Can't locate Math/FFT.pm in @INC (you may need to install the Math::FFT module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at -e line 1.
BEGIN failed--compilation aborted at -e line 1.

---

### Post by TheFu on 2014-08-29
It is a bad idea to mix OS perl and cpan modules.
The best practice is to use 1 of the other:
a) stay 100% with Ubuntu packages - they often start with "perl-", but unpopular modules may not exist.
b) install a self-contained perl with perlbrew [http://perlbrew.pl/](http://perlbrew.pl/) and use cpan to your heart's content. This method will not interfere with the OS installed perl or OS installed perl packages.

Enjoy.

BTW - this *best practice* applies to Ruby, Python, and other scripting languages as well.

---

### Post by bobmounger on 2014-08-29
actually, I did sudo cpan install Math::FFT & it is working : )

---

### Post by TheFu on 2014-08-30
For now.

libmath-fft-perl is the OS package I think you really wanted.  

I hope it doesn't cause issue if/when updates are needed.  New releases of Perl are changing things and CPAN authors are migrating their code to support the newer perl releases - 5.20 has lots of changes.  Also pay attention to deprecation warnings. There is only a 6 month notice required before removing features, though it is hoped that longer transitions will be allowed.

---

