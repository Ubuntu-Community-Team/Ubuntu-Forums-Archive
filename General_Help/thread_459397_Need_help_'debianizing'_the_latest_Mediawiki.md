---
title: "Need help 'debianizing' the latest Mediawiki"
date: 2007-05-30
forum: General Help
---

### Post by wsl3 on 2007-05-30
I am using Dapper, and want to custom roll MediaWiki 1.10.0 in the same way that 1.7 was rolled.

I have installed fakeroot, dh-make, and build-essential. I have fetched the sources for 1.7 by issuing 'apt-get source mediawiki'.

I have grabbed the latest tarball for Mediawiki, and extracted it. I have changed to the directory in question and issued a dh_make:
```
root@ubuntu-xen-dev:/usr/local/src/mediawiki-1.10.0# dh_make

Type of package: single binary, multiple binary, library, kernel module or cdbs?
 [s/m/l/k/b] s

Maintainer name : root
Email-Address   : root@unknown
Date            : Wed, 30 May 2007 20:50:34 +0000
Package Name    : mediawiki
Version         : 1.10.0
License         : blank
Type of Package : Single
Hit <enter> to confirm:
Done. Please edit the files in the debian/ subdirectory now. You should also
check that the mediawiki Makefiles install into $DESTDIR and not in / .

```It is at this point that the process breaks down. Copying files out of the original debian directory in the 1.7 tree cause problems when I then issue a 'fakeroot debian/rules binary' resulting in:

```
/usr/bin/env: php: No such file or directory
/usr/bin/env: php: No such file or directory
/usr/bin/env: php: No such file or directory
/usr/bin/env: php: No such file or directory
/usr/bin/env: php: No such file or directory
/usr/bin/env: php: No such file or directory

... MUCH garbage repeating clipped ...

#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
#     Failed test (t/maint/php-lint.t at line 31)
# Looks like you failed 628 tests of 628.
Can't locate File/Slurp.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at t/maint/php-tag.t line 8.
BEGIN failed--compilation aborted at t/maint/php-tag.t line 8.
# Looks like your test died before it could output anything.
Can't locate File/Slurp.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at t/maint/unix-newlines.t line 8.
BEGIN failed--compilation aborted at t/maint/unix-newlines.t line 8.
# Looks like your test died before it could output anything.
Failed 9/10 test scripts, 10.00% okay. 628/1409 subtests failed, 55.43% okay.
make[1]: *** [test] Error 255
make: *** [build-stamp] Error 2

```HELP!

---

### Post by MoLE on 2007-06-07
I'd love to see someone go through this process step-by-step too, as this is one of the areas which my knowledge is rather deficient.

I'm not sure if the [Deb Guide]("http://doc.gwos.org/index.php/Deb_Guide") is of any use to you?

---

