---
title: "Upgrade to 15.10, no libapache2-mod-suphp?"
date: 2015-10-22
forum: General Help
---

### Post by Ken-san on 2015-10-22
Hi all, I just upgraded to 15.10 and apparently didn't check the list of software to remove when upgrading, because after booting up again, I found that libapache2-mod-suphp is no longer installed and can't be installed either.

Any workarounds to install the version that 15.04 had in the meantime? Thanks in advance.

---

### Post by mercvrivs on 2015-11-10
As seen here: [https://www.howtoforge.com/tutorial/ubuntu-perfect-server-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/2/](https://www.howtoforge.com/tutorial/ubuntu-perfect-server-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/2/)

> 
8.4 Install SuPHP (optional, not recommended)
SuPHP is not available anymore for Debian Jessie. The suphp mode should not be used anymore in ISPConfig as there are better PHP modes like php-fpm and php-fcgi available. If you really need suphp for legacy reasons, then follow the steps in this chapter to compile it manually:




---

### Post by saldanhakun on 2015-12-07
I've updated from vivid to wily, and also found that out the hard way.
I have tried to configure fastcgi+php-fpm, using [this "Perfect Server" article]("https://www.howtoforge.com/tutorial/ubuntu-perfect-server-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/2/#-install-suphp-optional-not-recommended"), but since I'm not intended to use ISPconfig, this just was too much trouble. suphp, dead as it is, was just simpler and fit my needs better.

So, I reverted much of what I've installed, and just tried to install Trusty's packages for suPHP. And it works out of the box!
There are 2 packages, which should be easy enough to install: [suphp-common]("https://launchpad.net/ubuntu/trusty/amd64/suphp-common/0.7.2-0ubuntu1") and [libapache2-mod-suphp]("https://launchpad.net/ubuntu/wily/amd64/libapache2-mod-suphp/0.7.2-0ubuntu1"). Download from the "Downloadable files" section on the right. Install suphp-common first. I've used GDebi (on Mint Linux), but dpkg or maybe even apt-get would do the job just fine.

On my box, suphp-common installed without any issues, and libapache2-mod-suphp conflicted with libapache2-mod-ruid2 ([some kind of suphp alternative]("https://github.com/mind04/mod-ruid2") I was trying), which after removed was no more an issue.

Hope this can help somebody.

---

