---
title: "Making Xapian 1.2.15 in PHP 5.5 work (on nginx)"
date: 2013-11-01
forum: General Help
---

### Post by sebagr on 2013-11-01
Ubuntu 13.10 comes with PHP 5.5 by default (yay!) but for Xapian users this means we need to recompile the xapian-bindings and currently it seems nobody wrote how to do this, so I decided to share my findings for those who need it.

Basically, the steps are very similar than [those for PHP 5.4]("http://trac.xapian.org/wiki/FAQ/PHP%20Bindings%20Package"), but **Lintian ends up displaying a [bad-distribution-in-changes-file]("http://lintian.debian.org/tags/bad-distribution-in-changes-file.html")** error at the end (actually, I don't know if this message also appears for PHP 5.4 or not because I didn't try).

When I saw this error I thought something failed and spent quite some time browsing for help and there was nothing. However, [B]I found this error is not crucial (it's just complaining about the changelog).

The package still gets built[/B] so if you see this error you can happily ignore it if you're not distributing this package or don't care about the changelog.

These are the steps I used to build xapian-bindings (1.2.15) for PHP 5.5 under Ubuntu 13.10, and make Lintian happy:


```

**# Get the source and configure it**
sudo apt-get update
sudo apt-get build-dep xapian-bindings
sudo apt-get install php5-dev php5-cli devscripts
apt-get source xapian-bindings
cd xapian-bindings-1.2.*
rm -f debian/control debian/*-stamp
env PHP_VERSIONS=5 debian/rules maint
sed -i 's!include_path=php5$!include_path=$(srcdir)/php5!' php/Makefile.in
echo auto-commit >> debian/source/options

**# Make Lintian happy**
sed -i 's/unstable;/saucy;/' debian/changelog

**# Build the .deb package**
env DEB_BUILD_OPTIONS=nocheck debuild -e PHP_VERSIONS=5 -us -uc 

**# Install the built package**
cd ..
sudo dpkg -i php5-xapian_*.deb

```


Additionally, being a complete newbie with nginx, I couldn't make it work on my website initially. I found that I had to make the new extension available to fpm first:

```

[B]# Make Xapian extension load in php-fpm
[/B]cd /etc/php5/fpm/conf.d
ln -s ../../mods-available/xapian.ini ./20-xapian.ini

[B]# Restart nginx
[/B]sudo service php5-fpm restart

```

Hope this helps someone!

Keywords: PHP 5.5, Xapian, xapian-bindings, bad-distribution-in-changes-file, Ubuntu 13.10

---

