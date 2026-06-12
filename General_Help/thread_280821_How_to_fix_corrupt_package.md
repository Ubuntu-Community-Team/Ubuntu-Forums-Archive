---
title: "How to fix corrupt package"
date: 2006-10-20
forum: General Help
---

### Post by Robbi_az on 2006-10-20
Heya,

I just installed a fresh copy of Dapper with KDE! But am having trouble as below...

robbi@Robbi:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
amarok: Depends: amarok-xine but it is not going to be installed
Depends: ruby but it is not going to be installed
Depends: python-qt3 but it is not going to be installed
Depends: libifp4 but it is not going to be installed
Depends: libtunepimp3 (>= 0.4.2) but it is not going to be installed
Depends: libvisual-0.4-0 (>= 0.4.0) but it is not going to be installed
kdm: Depends: kdebase-bin (= 4:3.5.2-0ubuntu27) but 4:3.5.3-0ubuntu0.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

--------------------------------------------------

So, i thoguht why not... and gave it a go...

--------------------------------------------------


robbi@Robbi:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
kdm
0 upgraded, 0 newly installed, 1 to remove and 20 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1503kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing kdm (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
what(): basic_string::_S_construct NULL not valid
Aborted
robbi@Robbi:~$ Errors were encountered while processing:
kdm

-------------------------------------------------

so, tried going in to synaptic and marking for reinstallation.... and i got the following...

E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory

Then tried marking it for removal.. thyinking i could jsut reinstall afterwards, but i got the following...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

so... When i tried it...

robbi@Robbi:~$ sudo dpkg --configure -a
robbi@Robbi:~$

.. seems to have done absolutely nothing... !

Then i read in another thread to do with fixing broken packages to try//

robbi@Robbi:~$sudo aptitude remove -f

but that gave me the following...

robbi@Robbi:~$ sudo aptitude remove -f
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  kdm
The following packages have been kept back:
  automatix2 karbon kchart kexi kformula kivio kivio-data koffice
  koffice-data koffice-libs koshell kpresenter kpresenter-data krita
  krita-data kspread kthesaurus kugar kword kword-data
0 packages upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
Need to get 0B/615kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  kdm: Depends: kdebase-bin (= 4:3.5.2-0ubuntu27) but 4:3.5.3-0ubuntu0.2 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
kdm

Score is -301

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  kdm
The following packages have been kept back:
  automatix2 karbon kchart kexi kformula kivio kivio-data koffice
  koffice-data koffice-libs koshell kpresenter kpresenter-data krita
  krita-data kspread kthesaurus kugar kword kword-data
The following packages will be REMOVED:
  kdm
0 packages upgraded, 0 newly installed, 1 to remove and 20 not upgraded.
Need to get 0B of archives. After unpacking 1503kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing kdm (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
robbi@Robbi:~$ Errors were encountered while processing:
 kdm


**Can anyone please please please please help me ?**

---

### Post by factotum218 on 2006-10-20
at this point i would be curled up in a whimpering ball giving up and just intalling kubuntu-desktop

---

