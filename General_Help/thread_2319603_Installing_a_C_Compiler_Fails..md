---
title: "Installing a C Compiler Fails."
date: 2016-04-05
forum: General Help
---

### Post by andrew292 on 2016-04-05
I want to install Winbind from source, on a default installation of Ubuntu 12.04. Can anyone explain the following ?
```

root@ir-dept-1:/var/run/samba# sudo apt-get install gcc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gcc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'gcc' has no installation candidate
root@ir-dept-1:/var/run/samba# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: gcc (>= 4:4.4.3) but it is not installable
                   Depends: g++ (>= 4:4.4.3) but it is not installable
E: Unable to correct problems, you have held broken packages.
root@ir-dept-1:/var/run/samba#
```

---

### Post by TheFu on 2016-04-06
a) no need for sudo if you are root already.
b) Try updating everything first
```
aptitude update
aptitude upgrade
aptitude install gcc

```
and post the errors, if any.  I suspect that a .deb file was manually installed which was dependent on an older g++, so it may be required to remove that older package. Aptitude will try harder than apt-get to find a solution - be certain to carefully read the solution that is offered. It is ok to reject some and aptitude will probably offer another solution.

Should still have a yr of support left on 12.04, but it is time to start planning the migration. ;)  I have 1 box left on 12.04 still too.

---

### Post by HermanAB on 2016-04-06
Simply install the package 'build-essential'.  That will give you everything you need to compile software.

$ sudo apt-get build-essential

That's all.

---

