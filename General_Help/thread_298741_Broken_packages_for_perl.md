---
title: "Broken packages for perl"
date: 2006-11-13
forum: General Help
---

### Post by glave on 2006-11-13
I'm trying to install perl-suid but I keep getting a broken packages error:

```
root@arcade:~# sudo apt-get install perl-suid
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  perl-suid: Depends: perl (= 5.8.7-5ubuntu1) but 5.8.7-5ubuntu1.2 is to be installed
             Depends: libperl5.8 (= 5.8.7-5ubuntu1) but it is not going to be installed
E: Broken packages
root@arcade:~#
```

Looking at other posts about broken packages, I tried to remove perl, but that was going to uninstall half my friggin system along with it! This is a server install, so I can't use the nice little 'Fix Broken Packages' click of Synaptic. 

Anyone have some pointers on this?

---

### Post by glave on 2006-11-18
Still trying to hash this one out. Anyone?

---

