---
title: "libssl-dev broken after Heartbleed patch"
date: 2014-07-25
forum: General Help
---

### Post by atatistcheff on 2014-07-25
Ok I am sure I'm not the first person to encounter this but my search for libssl-dev came up with no answers.  I have run into a dependency loop on my 12.04 system and apt-get will no longer update several packages.  When running "apt-get upgrade" I get the following:

```
root@ubuntuesxi:/home/alext# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.13) but 1.0.1-4ubuntu5.16 is installed
E: Unmet dependencies. Try using -f.
```

All attempts to upgrade/remove the SSL components are failing because of the broken dependencies.  For instance if I try to remove libssl-dev or php5-dev I run into the following errors:
```
root@ubuntuesxi:/home/alext# apt-get remove libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 php5-dev : Depends: libssl-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntuesxi:/home/alext# 
root@ubuntuesxi:/home/alext# 
root@ubuntuesxi:/home/alext# apt-get remove php5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.13) but 1.0.1-4ubuntu5.16 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntuesxi:/home/alext# 
```

I have of course tried all the suggested commands with -f.  I am willing to uninstall/reinstall whatever is necessary but it seems like I'm in a Catch-22 situation.  How can I deal with packages that have a dependency on an SSL library that has been updated?

Thanks!

---

### Post by bapoumba on 2014-07-28
Broken dependencies are often linked to using ppas or third party repositories.
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

