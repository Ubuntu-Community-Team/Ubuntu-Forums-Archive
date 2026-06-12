---
title: "debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /et"
date: 2013-07-31
forum: General Help
---

### Post by desesperado on 2013-07-31
Today, after executing **sudo apt-get update && sudo apt-get dist-upgrade** in tty1 I got stuck in a hurricane of errors. I'm getting
 ```
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at (eval 1) line 2. BEGIN failed--compilation aborted at (eval 1) line 2

```
Also there are major errors with:
python3-software-properties
software-properties-common
software-properties-gtk

The output of **sudo dpkg --audit** is:
```
The following packages are in a mess due to serious problems during installation. They must be reinstalled for them (and any packages that depend on them) to function properly:
software-properties-common
python3-software-properties
software-properties-gtk

The following packages are only half configured probably due to problems configuring them the first time. The configuration should be retried using dpkg --configure <package> or the configure menu option in dselect:
man-db
lightdm
mime-support
```

I've already tried to no avail, I don't seem to get anywhere but to the same point:
```
sudo ap-get -f install
sudo dpkg --configure -a
sudo apt-get install --reinstall (each one of them)
```

The output of lsb_release -a && uname -r is:
```
No LSB modules are available
Distributor ID: Ubuntu
Description: Ubuntu 13.10
Release: 13.10
Codename: saucy
3.11.0-031100rc1-generic
```

---

### Post by desesperado on 2013-08-01
Bump. 

Isn't there no one that can help me?!

---

