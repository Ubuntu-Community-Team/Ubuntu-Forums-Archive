---
title: "RHEL Admin catching back up w/ Ubuntu"
date: 2013-03-28
forum: General Help
---

### Post by uberlinux on 2013-03-28
Hello All,

I was around for 4.10 through 8.04, then started administering RedHat Enterprise Linux professionally and haven't touched Ubuntu in 5 years.  I'm a fairly decent RedHat admin at this point but am incredibly rusty w/ Debian-based administration.  Are there resources with my situation in mind?  

With the growing popularity of Ubuntu, it seems this must be a common scenerio for experienced Solaris/AIX / RedHat / SuSE admins who need to get up to speed with Ubuntu due to changing environments at work.  

This situation reminds me of the 90s when a lot of books came out tailored for experienced Unix admins moving to RedHat.  


Thanks!

---

### Post by schragge on 2013-03-28
See [uhelp]community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora[/uhelp]
It's not quite up to date, but still helpful.
Also, the official Ubuntu Server Guide ([uhelp]12.10/serverguide[/uhelp]), [Debian Reference](http://www.debian.org/doc/manuals/debian-reference/index.en.html), and [uhelp]community/NewDocs[/uhelp] are good starting points.

If you have any specific questions along the lines "I do it so and so in RHEL, how will I do the same in Ubuntu", don't hesitate to ask.

---

### Post by uberlinux on 2013-03-28
Thanks!  

The network stuff is most useful.  I might want to throw up a cheat sheet at some point.

---

### Post by SeijiSensei on 2013-03-28
I've found the biggest differences concern the locations and names of key files.  Ubuntu server tends to have more in /etc than RedHat does.  For instance, the default chrooted BIND server lives in /var/named/chroot while in Ubuntu BIND configurations are in /etc/bind.  The default website DocumentRoot is /var/www in Ubuntu rather than /var/www/html.  Apache configurations in Ubuntu are in /etc/apache2 rather than /etc/httpd.  Ubuntu also has a tendency to append version numbers to some log file directories like /var/log/apache2 and /var/log/squid3.  Log files have different names -- /var/log/maillog becomes /var/log/mail.log.  /var/log/messages is /var/log/syslog.  

In general I've become more enamored with apt over yum as time goes on, too.  Yum often takes a long time to actually begin downloading the files you need while it searches all the repositories and builds the appropriate index files.  "apt-get update" handles that task, and the results persist, so you can come back and download another .deb without waiting for the indexes to be updated again as yum seems to do.

I still use CentOS pretty much exclusively on servers because some of the packages I use are better matched to RedHat-flavored machines.  This is especially true for [MailScanner]("http://www.mailscanner.info/").

---

### Post by schragge on 2013-03-28
For me, the biggest differences by far are in package naming. [Debian Policy]("http://www.debian.org/doc/debian-policy/") prescribes renaming of many classes of packages, while those on RedHat often retain pristine upstream names. E.g. all package names [must be lowercase]("http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Source"); all library package names on Debian [must]("http://www.debian.org/doc/debian-policy/ch-sharedlibs.html#s-sharedlibs-runtime") start with *lib* and often contain version as part of their name, so *glibc* is *libc6*; all python modules [must]("http://www.debian.org/doc/packaging-manuals/python-policy/ch-module_packages.html#s-package_names") start in *python-*, so *PyCrypto* is *python-crypto*; all perl modules [must]("http://www.debian.org/doc/packaging-manuals/perl-policy/ch-module_packages.html#s-package_names") start with *lib* and end in *-perl*, java libraries [must]("http://www.debian.org/doc/packaging-manuals/java-policy/x104.html") be named *libXXX-java*, and so on. It's actually easier once you know the rules as all packages are uniformly named, but for somebody who is new to Debian and tries to compile something from source following upstream instructions, chasing down dependencies of a package may be rather a challenging task. Fortunately, there is [distromatch](http://dde.debian.net/distromatch-frontend.html).

That said, I'm on pure Debian, and use neither upstart nor AppArmor.

---

