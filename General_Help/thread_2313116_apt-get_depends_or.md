---
title: "apt-get depends or"
date: 2016-02-09
forum: General Help
---

### Post by ashley.bye on 2016-02-09
I want to install FusionDirectory, which is a package in the Ubuntu repositories.  The [package details]("http://packages.ubuntu.com/wily/web/fusiondirectory") show that it depends on apache2 or nginx or a couple of others.  I already have nginx installed and don't want to run apache alongside it.  How do I specify that I want to use this instead of apache2, which seems to be the default option?

If I use:

```
sudo apt-get build-dep nginx install fusiondirectory
```

I get the following response:

> [COLOR=#839496][FONT=Menlo][/FONT][/COLOR]Reading package lists... DoneBuilding dependency tree
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

I don't know what source URIs it is referring to, and I can quite happily install FusionDirectory with the build-dep, apart from the clash with nginx which is already running.

I'd appreciate any help that can be provided.

---

### Post by oldos2er on 2016-02-09
Can we see your sources.list? ```
cat /etc/apt/sources.list
```

---

### Post by ashley.bye on 2016-02-10
Here it is:

```
cat /etc/apt/sources.list 
# deb cdrom:[Ubuntu-Server 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20160205)]/ xenial main restricted
# deb cdrom:[Ubuntu-Server 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20160205)]/ xenial main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb [http://ossec.wazuh.com/repos/apt/ubuntu](http://ossec.wazuh.com/repos/apt/ubuntu) trusty main
```

---

### Post by steeldriver on 2016-02-10
Why are build-deps involved at all, here? build dependencies are not generally required when you're installing a binary package

---

### Post by oldos2er on 2016-02-10
Please use the default font and color for your posts; it's much easier for others to read.

A couple things; you have no source repositories enabled (deb-src), which is why build-dep complained about having no URIs to work with. However you seem to be wanting *sudo apt-get install fusiondirectory* instead of build-dep?

Also you're running Xenial which at this point in its development should only be used for testing purposes. 

And I would get rid of the trusty repo "deb [http://ossec.wazuh.com/repos/apt/ubuntu"]("http://ossec.wazuh.com/repos/apt/ubuntu"). Mixing repos for different Ubuntu versions is rarely if ever a good idea.

---

### Post by ashley.bye on 2016-02-11
I wasn't aware I hadn't used default fonts or colours; I've not changed any settings.  It might be where I've copied and pasted from Terminal so I'll just set everything to be black.

If I look at the package details for fusiondirectory:

```
[FONT=Menlo]apt-cache show fusiondirectoryPackage: fusiondirectory[/FONT]
[FONT=Menlo]Priority: optional[/FONT]
[FONT=Menlo]Section: universe/web[/FONT]
[FONT=Menlo]Installed-Size: 6845[/FONT]
[FONT=Menlo]Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>[/FONT]
[FONT=Menlo]Original-Maintainer: FusionDirectory packages maintainers group <packages@lists.fusiondirectory.org>[/FONT]
[FONT=Menlo]Architecture: all[/FONT]
[FONT=Menlo]Version: 1.0.8.8-3[/FONT]
[FONT=Menlo]Replaces: fusiondirectory-plugin-dashboard (<< 1.0.8.7), fusiondirectory-plugin-dashboard-schema (<< 1.0.8.7)[/FONT]
[FONT=Menlo]Depends: apache2 | lighttpd | httpd | nginx, fusiondirectory-smarty3-acl-render, gettext, javascript-common, libarchive-extract-perl, libcrypt-cbc-perl, libcrypt-passwdmd5-perl, libfile-copy-recursive-perl, libjs-prototype, libjs-scriptaculous, libnet-ldap-perl, libpath-class-perl, libterm-readkey-perl, libxml-twig-perl, php-fpdf, php5, php5-cli, php5-curl, php5-gd, php5-imagick, php5-imap, php5-ldap, php5-mcrypt, php5-recode, schema2ldif, smarty-gettext (>= 1.1), smarty3[/FONT]
[FONT=Menlo]Suggests: argonaut-server, fusiondirectory-schema (= 1.0.8.8-3), slapd[/FONT]
[FONT=Menlo]Conflicts: gosa[/FONT]
[FONT=Menlo]Breaks: fusiondirectory-plugin-dashboard (<< 1.0.8.7), fusiondirectory-plugin-dashboard-schema (<< 1.0.8.7)[/FONT]
[FONT=Menlo]Filename: pool/universe/f/fusiondirectory/fusiondirectory_1.0.8.8-3_all.deb[/FONT]
[FONT=Menlo]Size: 686760[/FONT]
[FONT=Menlo]MD5sum: 7d01613a788f241f2e303a06dcd7fd7b[/FONT]
[FONT=Menlo]SHA1: 4eb28f64774b793a0d0e945789eb9d21960bb0f6[/FONT]
[FONT=Menlo]SHA256: f81ad1b5cf1a150306c4c7774b2e7e0049490d8a5f00500283a7bda7cc52d19c[/FONT]
[FONT=Menlo]Description-en: Web Based LDAP Administration Program[/FONT]
[FONT=Menlo] Provided is access to posix, shadow, samba, proxy, fax, pureftp and[/FONT]
[FONT=Menlo] kerberos accounts. It is able to manage the postfix/cyrus server[/FONT]
[FONT=Menlo] combination and can write user adapted sieve scripts.[/FONT]
[FONT=Menlo] .[/FONT]
[FONT=Menlo] FusionDirectory is a combination of system-administrator and end-user web[/FONT]
[FONT=Menlo] interface, designed to handle LDAP based network infrastructures.[/FONT]
[FONT=Menlo]Description-md5: bab090f117ae2eb977b8c2ea09f4279d[/FONT]
[FONT=Menlo]Homepage: http://www.fusiondirectory.org/[/FONT]
[FONT=Menlo]Bugs: https://bugs.launchpad.net/ubuntu/+filebug[/FONT]
[FONT=Menlo]Origin: Ubuntu[/FONT]
```

It shows that it [FONT=Menlo]*Depends: apache2 | lighttpd | httpd | nginx*. How do I specify that I want to depend on nginx rather than apache2?[/FONT]

---

### Post by oldos2er on 2016-02-11
See what ```
sudo apt-get install -s fusiondirectory
``` says. The "-s" switch means the install will only be simulated.

---

### Post by ashley.bye on 2016-02-12
[SIZE=3][FONT=arial]```
sudo apt-get install -s fusiondirectory

```[/FONT]```
[FONT=Menlo][FONT=arial][sudo] password for administrator: [/FONT][/FONT]
[FONT=Menlo][FONT=arial]Reading package lists... Done[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Building dependency tree       [/FONT][/FONT]
[FONT=Menlo][FONT=arial]Reading state information... Done[/FONT][/FONT]
[FONT=Menlo][FONT=arial]The following additional packages will be installed:[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  apache2 apache2-bin apache2-data apache2-utils fontconfig-config fonts-dejavu-core fusiondirectory-smarty3-acl-render gettext ghostscript imagemagick-common javascript-common[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libapache2-mod-php5 libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libarchive-extract-perl libasprintf-dev libasprintf0v5 libavahi-client3 libavahi-common-data[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libavahi-common3 libcroco3 libcrypt-cbc-perl libcrypt-passwdmd5-perl libcrypt-rijndael-perl libcups2 libcupsfilters1 libcupsimage2 libcurl3 libfftw3-double3[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libfile-copy-recursive-perl libfontconfig1 libgd3 libgettextpo-dev libgettextpo0 libgs9 libgs9-common libijs-0.35 libjbig0 libjbig2dec0 libjpeg-turbo8 libjpeg8[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libjs-prototype libjs-scriptaculous liblcms2-2 liblqr-1-0 libltdl7 liblua5.1-0 libmagickcore-6.q16-2 libmagickwand-6.q16-2 libmcrypt4 libpaper-utils libpaper1[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libpath-class-perl librecode0 libterm-readkey-perl libtie-ixhash-perl libtiff5 libunistring0 libvpx3 libxml-twig-perl libxml-xpathengine-perl libxpm4 php-fpdf php5 php5-curl[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  php5-gd php5-imagick php5-ldap php5-mcrypt php5-recode poppler-data smarty-gettext smarty3 ssl-cert ttf-dejavu-core[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Suggested packages:[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  apache2-doc apache2-suexec-pristine | apache2-suexec-custom argonaut-server slapd gettext-doc autopoint ghostscript-x hpijs cups-common libfftw3-bin libfftw3-dev libgd-tools[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  fonts-droid texlive-lang-cjk liblcms2-utils libmagickcore-6.q16-2-extra libmcrypt-dev mcrypt libunicode-map8-perl libunicode-string-perl xml-twig-tools ttf2pt1 poppler-utils[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  fonts-japanese-mincho | fonts-ipafont-mincho fonts-japanese-gothic | fonts-ipafont-gothic fonts-arphic-ukai fonts-arphic-uming fonts-nanum openssl-blacklist[/FONT][/FONT]
[FONT=Menlo][FONT=arial]The following NEW packages will be installed[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  apache2 apache2-bin apache2-data apache2-utils fontconfig-config fonts-dejavu-core fusiondirectory fusiondirectory-smarty3-acl-render gettext ghostscript imagemagick-common[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  javascript-common libapache2-mod-php5 libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libarchive-extract-perl libasprintf-dev libavahi-client3[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libavahi-common-data libavahi-common3 libcroco3 libcrypt-cbc-perl libcrypt-passwdmd5-perl libcrypt-rijndael-perl libcups2 libcupsfilters1 libcupsimage2 libcurl3[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libfftw3-double3 libfile-copy-recursive-perl libfontconfig1 libgd3 libgettextpo-dev libgettextpo0 libgs9 libgs9-common libijs-0.35 libjbig0 libjbig2dec0 libjpeg-turbo8[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libjpeg8 libjs-prototype libjs-scriptaculous liblcms2-2 liblqr-1-0 libltdl7 liblua5.1-0 libmagickcore-6.q16-2 libmagickwand-6.q16-2 libmcrypt4 libpaper-utils libpaper1[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libpath-class-perl librecode0 libterm-readkey-perl libtie-ixhash-perl libtiff5 libunistring0 libvpx3 libxml-twig-perl libxml-xpathengine-perl libxpm4 php-fpdf php5 php5-curl[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  php5-gd php5-imagick php5-ldap php5-mcrypt php5-recode poppler-data smarty-gettext smarty3 ssl-cert ttf-dejavu-core[/FONT][/FONT]
[FONT=Menlo][FONT=arial]The following packages will be upgraded:[/FONT][/FONT]
[FONT=Menlo][FONT=arial]  libasprintf0v5[/FONT][/FONT]
[FONT=Menlo][FONT=arial]1 to upgrade, 77 to newly install, 0 to remove and 48 not to upgrade.[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libapr1 (1.5.2-3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libaprutil1 (1.5.4-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libaprutil1-dbd-sqlite3 (1.5.4-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libaprutil1-ldap (1.5.4-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst liblua5.1-0 (5.1.5-8 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst apache2-bin (2.4.18-1ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst apache2-utils (2.4.18-1ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst apache2-data (2.4.18-1ubuntu1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst apache2 (2.4.18-1ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst imagemagick-common (8:6.8.9.9-7 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libfftw3-double3 (3.3.4-2ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libjpeg-turbo8 (1.4.2-0ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst liblcms2-2 (2.6-3ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst liblqr-1-0 (0.4.2-2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst fonts-dejavu-core (2.35-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst fontconfig-config (2.11.1-0ubuntu7 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libfontconfig1 (2.11.1-0ubuntu7 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libjbig0 (2.1-3.1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libjpeg8 (8c-2ubuntu8 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libltdl7 (2.4.6-0.1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libtiff5 (4.0.6-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libmagickcore-6.q16-2 (8:6.8.9.9-7 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libmagickwand-6.q16-2 (8:6.8.9.9-7 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libunistring0 (0.9.3-5.2ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libxpm4 (1:3.5.11-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst poppler-data (0.4.7-7 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libasprintf0v5 [0.19.7-2ubuntu2] (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libapache2-mod-php5 (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst php5 (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst smarty3 (3.1.21-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst fusiondirectory-smarty3-acl-render (1.0.8.8-3 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libcroco3 (0.6.11-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst gettext (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst javascript-common (11 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libarchive-extract-perl (0.76-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libcrypt-rijndael-perl (1.13-1build1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libcrypt-cbc-perl (2.33-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libcrypt-passwdmd5-perl (1.3-10 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libfile-copy-recursive-perl (0.38-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libjs-prototype (1.7.1-3 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libjs-scriptaculous (1.9.0-2 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libpath-class-perl (0.35-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libterm-readkey-perl (2.33-1build1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libxml-twig-perl (1:3.48-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst php-fpdf (3:1.7.dfsg-1.1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libcurl3 (7.47.0-1ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst php5-curl (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libvpx3 (1.5.0-2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libgd3 (2.1.1-4build2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst php5-gd (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst php5-imagick (3.3.0~rc2-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst php5-ldap (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libmcrypt4 (2.5.8-3.3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst php5-mcrypt (5.4.6-0ubuntu6 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst librecode0 (3.6-22 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst php5-recode (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst smarty-gettext (1.2.0-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst fusiondirectory (1.0.8.8-3 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libavahi-common-data (0.6.32~rc+dfsg-1ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libavahi-common3 (0.6.32~rc+dfsg-1ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libavahi-client3 (0.6.32~rc+dfsg-1ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libcups2 (2.1.2-2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libcupsfilters1 (1.8.1-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libcupsimage2 (2.1.2-2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libijs-0.35 (0.35-11 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libjbig2dec0 (0.12+20150918-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libpaper1 (1.1.24+nmu4ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libgs9-common (9.16~dfsg~0-0ubuntu4 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libgs9 (9.16~dfsg~0-0ubuntu4 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst ghostscript (9.16~dfsg~0-0ubuntu4 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libasprintf-dev (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libgettextpo0 (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libgettextpo-dev (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libpaper-utils (1.1.24+nmu4ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libtie-ixhash-perl (1.23-2 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst libxml-xpathengine-perl (0.13-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst ssl-cert (1.0.37 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Inst ttf-dejavu-core (2.35-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libapr1 (1.5.2-3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libaprutil1 (1.5.4-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libaprutil1-dbd-sqlite3 (1.5.4-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libaprutil1-ldap (1.5.4-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf liblua5.1-0 (5.1.5-8 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf apache2-bin (2.4.18-1ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf apache2-utils (2.4.18-1ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf apache2-data (2.4.18-1ubuntu1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf apache2 (2.4.18-1ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf imagemagick-common (8:6.8.9.9-7 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libfftw3-double3 (3.3.4-2ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libjpeg-turbo8 (1.4.2-0ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf liblcms2-2 (2.6-3ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf liblqr-1-0 (0.4.2-2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf fonts-dejavu-core (2.35-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf fontconfig-config (2.11.1-0ubuntu7 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libfontconfig1 (2.11.1-0ubuntu7 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libjbig0 (2.1-3.1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libjpeg8 (8c-2ubuntu8 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libltdl7 (2.4.6-0.1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libtiff5 (4.0.6-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libmagickcore-6.q16-2 (8:6.8.9.9-7 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libmagickwand-6.q16-2 (8:6.8.9.9-7 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libunistring0 (0.9.3-5.2ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libxpm4 (1:3.5.11-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf poppler-data (0.4.7-7 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libasprintf0v5 (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libapache2-mod-php5 (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf php5 (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf smarty3 (3.1.21-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf fusiondirectory-smarty3-acl-render (1.0.8.8-3 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libcroco3 (0.6.11-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf gettext (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf javascript-common (11 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libarchive-extract-perl (0.76-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libcrypt-rijndael-perl (1.13-1build1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libcrypt-cbc-perl (2.33-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libcrypt-passwdmd5-perl (1.3-10 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libfile-copy-recursive-perl (0.38-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libjs-prototype (1.7.1-3 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libjs-scriptaculous (1.9.0-2 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libpath-class-perl (0.35-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libterm-readkey-perl (2.33-1build1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libxml-twig-perl (1:3.48-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf php-fpdf (3:1.7.dfsg-1.1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libcurl3 (7.47.0-1ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf php5-curl (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libvpx3 (1.5.0-2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libgd3 (2.1.1-4build2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf php5-gd (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf php5-imagick (3.3.0~rc2-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf php5-ldap (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libmcrypt4 (2.5.8-3.3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf php5-mcrypt (5.4.6-0ubuntu6 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf librecode0 (3.6-22 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf php5-recode (5.6.17+dfsg-3ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf smarty-gettext (1.2.0-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf fusiondirectory (1.0.8.8-3 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libavahi-common-data (0.6.32~rc+dfsg-1ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libavahi-common3 (0.6.32~rc+dfsg-1ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libavahi-client3 (0.6.32~rc+dfsg-1ubuntu2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libcups2 (2.1.2-2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libcupsfilters1 (1.8.1-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libcupsimage2 (2.1.2-2 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libijs-0.35 (0.35-11 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libjbig2dec0 (0.12+20150918-1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libpaper1 (1.1.24+nmu4ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libgs9-common (9.16~dfsg~0-0ubuntu4 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libgs9 (9.16~dfsg~0-0ubuntu4 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf ghostscript (9.16~dfsg~0-0ubuntu4 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libasprintf-dev (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libgettextpo0 (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libgettextpo-dev (0.19.7-2ubuntu3 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libpaper-utils (1.1.24+nmu4ubuntu1 Ubuntu:16.04/xenial [amd64])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libtie-ixhash-perl (1.23-2 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf libxml-xpathengine-perl (0.13-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf ssl-cert (1.0.37 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
[FONT=Menlo][FONT=arial]Conf ttf-dejavu-core (2.35-1 Ubuntu:16.04/xenial [all])[/FONT][/FONT]
```[/SIZE]

---

### Post by ian-weisser on 2016-02-12
> **ashley.bye said:**
> [FONT=Menlo][/FONT]
[FONT=Menlo]Depends: [...] | nginx, fusiondirectory-smarty3-acl-render, gettext, javascript-common, libarchive-extract-perl, libcrypt-cbc-perl, libcrypt-passwdmd5-perl, libfile-copy-recursive-perl, libjs-prototype, libjs-scriptaculous, libnet-ldap-perl, libpath-class-perl, libterm-readkey-perl, libxml-twig-perl, php-fpdf, php5, php5-cli, php5-curl, php5-gd, php5-imagick, php5-imap, php5-ldap, php5-mcrypt, php5-recode, schema2ldif, smarty-gettext (>= 1.1), smarty3[/FONT]

Do you have all those other dependencies installed?

---

### Post by ashley.bye on 2016-02-13
No, not until I install fusion directory.

---

