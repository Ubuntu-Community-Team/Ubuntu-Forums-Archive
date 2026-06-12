---
title: "aptitude will not unhold packages"
date: 2008-04-30
forum: General Help
---

### Post by CSMatt on 2008-04-30
During my updates I decided to have aptitude hold the nexuiz and nexuiz-data packages because they are only backports and their large size make them a low priority right now.  Now that I'm done, I told aptitude to unhold the packages.  However, it doesn't appear that aptitude even noticed the unhold command, as the nexuiz and nexuiz-data packages are still being held back.  To make matters worse, now clamav packages are being held back, and trying to unhold clamav doesn't work either.
```
$ sudo aptitude safe-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  clamav-freshclam nexuiz-data 
The following packages have been kept back:
  clamav clamav-daemon clamtk nexuiz 
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
$ sudo aptitude unhold nexuiz 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  clamav-freshclam nexuiz-data 
The following packages have been kept back:
  clamav clamav-daemon clamtk nexuiz 
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
$ sudo aptitude safe-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  clamav-freshclam nexuiz-data 
The following packages have been kept back:
  clamav clamav-daemon clamtk nexuiz 
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
$
```
I'm using Ubuntu 7.10, by the way, not 8.04.

---

### Post by CSMatt on 2008-05-04
Bump.

---

### Post by capink on 2008-05-05
Try to directly edit the pkgstate file after backing it up as follows:

```
sudo cp -av /var/lib/aptitude/pkgstates{,_bak}
```

```
sudo gedit /var/lib/aptitude/pkgstates
```

In this file each package has an entry of multiple lines. Change the state field value form 2 (i.e hold) to 1 (i.e manually installed).

Save the file and exit and run the following command to see what aptitude would do:

```
sudo aptitude upgrade -s
```

---

### Post by CSMatt on 2008-05-06
The clamav packages have state 3 instead of state 1.  What does this mean?

---

### Post by capink on 2008-05-06
I think 3 means automatically installed package. That is this package only remains on the system because it satisfies a dependency of a manually installed package.

---

### Post by CSMatt on 2008-05-06
Hmmm.  So, how do I unhold these packages without removing their automatically-installed status?

PS:
```
$ aptitude safe-upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  clamav-freshclam 
The following packages have been kept back:
  clamav clamav-daemon clamtk 
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Would download/install/remove packages.
$
```

---

### Post by capink on 2008-05-06
Can you please give me the output of the following command:

```
cat /var/lib/aptitude/pkgstates
```

---

### Post by CSMatt on 2008-05-06
There were too many to list, so I omitted all but the packages in question:
```
Package: clamav-freshclam
Unseen: yes
State: 3
Dselect-State: 1
Remove-Reason: 0

Package: clamav-daemon
Unseen: yes
State: 3
Dselect-State: 1
Remove-Reason: 0

Package: clamav
Unseen: yes
State: 3
Dselect-State: 1
Remove-Reason: 0

Package: clamtk
Unseen: yes
State: 3
Dselect-State: 1
Remove-Reason: 0
```

---

### Post by capink on 2008-05-06
Nothing in the pkgstates prevent these packages from upgrading as they are not being held back.

The most probable cause for them not being upgraded is that their new versions have introduced new dependencies that needs more aggressive actions to satisfy them (e.g. removing packages), which safe-upgrade is no capable of fulfilling. If you still want to upgrade them, you can run one of these two commands:

```
sudo aptitude full-upgrade
```

OR

```
sudo aptitude install clamav clamav-daemon clamtk clamav-freshclam
```

---

### Post by CSMatt on 2008-05-06
```
$ aptitude install -s clamav clamav-daemon clamtk clamav-freshclam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libclamav2 
The following NEW packages will be automatically installed:
  libclamav3 libconfig-tiny-perl 
The following NEW packages will be installed:
  libclamav3 libconfig-tiny-perl 
The following packages will be upgraded:
  clamav clamav-daemon clamav-freshclam clamtk 
4 packages upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 1854kB of archives. After unpacking 561kB will be used.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.
$
```
Yep.  That's it. Changing the State field from 2 to 1 also worked for the nexuiz packages.  Thank you.

---

