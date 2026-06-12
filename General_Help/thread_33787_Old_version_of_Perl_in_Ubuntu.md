---
title: "Old version of Perl in Ubuntu"
date: 2005-05-12
forum: General Help
---

### Post by dolny on 2005-05-12
dolny@milkshake:~$ sudo apt-get  install -f  libperl5.8
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
  libperl5.8: Depends: perl-base (= 5.8.4-6ubuntu1) but 5.8.4-8 is to be installed
E: Broken packages


----

I need this libs for xchat and some other apps... help!

---

### Post by defkewl on 2005-05-12
$ apt-get install perl-base

Or try adding some more repositories with:
$ base-config

---

### Post by dolny on 2005-05-12
dolny@milkshake:~$ sudo apt-get install perl-base
Password:
Reading package lists... Done
Building dependency tree... Done
perl-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

at the moment...

Do you recommend any repositories?

---

