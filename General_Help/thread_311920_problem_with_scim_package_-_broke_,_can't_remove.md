---
title: "problem with scim package - broke , can't remove"
date: 2006-12-03
forum: General Help
---

### Post by benny@linux on 2006-12-03
when i am trying to update my ubuntu edgy , synaptic scream at me that i have broken packages and i must fix them before continue ,
when i going to synaptic and press on the fix all broken packages ,nothing happen,

so i found the broken package - scim (i understand that this package is needed for chi input support - i dont need it :) )

so then ive open a console and get this ..

[B]benny@LinuxBox:~$ sudo aptitude remove  scim
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  scim-gtk2-immodule 
The following packages will be REMOVED:
  scim 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1999kB will be freed.
The following packages have unmet dependencies:
  scim-gtk2-immodule: Depends: scim but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Upgrade the following packages:
scim [1.4.4-4ubuntu6 (now) -> 1.4.4-4ubuntu6 (edgy, edgy)]

Score is 1

Accept this solution? [Y/n/q/?] y
The following packages will be upgraded:
  scim 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/800kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: parse error, in file `/var/lib/dpkg/status' near line 26708 package `scim':
 `Depends' field, reference to `libfreetype6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 26708 package `scim':
 `Depends' field, reference to `libfreetype6': version contains ` '
[/B]

what to do now?

---

### Post by benny@linux on 2006-12-04
Anyone?

---

### Post by benny@linux on 2006-12-04
please somebody - i cant install any updates or any new programs because of this problem

---

### Post by unimatrix on 2007-09-01
Try looking in /etc/apt/sources.list and remove/comment out any malformed lines.

---

### Post by expatCM on 2007-09-01
I think you may also have installed some local language support when you put scim on your computer?   

In order to completely remove scim you need to also remove the language support (System / Administration / Language Support).   If you then reboot scim should be gone.  You may need the language support for some other reason though so you may need to consider putting the language back but not scim ......

This approach worked for me on one machine ...  I am sure that there will be better ways of doing this and perhaps others can add to this thread ...

---

### Post by DougieFresh4U on 2007-09-01
Try this, just change package name:
Ok, got it. Heres what I did in case any one would like to know:

dougie@DougiesLeanMachine:~$ sudo dpkg --force-remove-reinstreq --remove avast4workstation
dpkg - warning, overriding problem because --force enabled:
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
(Reading database ...
dpkg: serious warning: files list file for package `avast4workstation' missing, assuming package has no files currently installed.
189321 files and directories currently installed.)
Removing avast4workstation .

---

