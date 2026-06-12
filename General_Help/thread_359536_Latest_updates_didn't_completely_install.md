---
title: "Latest updates didn't completely install"
date: 2007-02-12
forum: General Help
---

### Post by mawdryn on 2007-02-12
Hi All,

Sorry for the long post...

I installed the latest updates and was reading here that people seem to be having problems with these updates... me included.

Using Ubuntu Edgy, there were ~80Mb of kernel updates the other night, so I set them off to install and went to bed. Didn't notice anything amiss until I went hunting for nVidia updates today. 

Problem is, even though the updates are installed, 'dpkg -s linux-generic' gives 2.6.17.11, my grub config and 'uname -r' still only shows 2.6.17.10 (system has been rebooted)

'sudo apt-get upgrade' spits the dummy about the linux-restricted-modules-generic package being kept back.

'sudo aptitude dist-upgrade' spits out the following:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-restricted-modules-2.6.17-11-generic 
The following packages will be upgraded:
  linux-restricted-modules-generic 
1 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7706kB of archives. After unpacking 20.9MB will be used.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.17-11-generic: Depends: linux-image-2.6.17-11-generic which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-generic
linux-restricted-modules-generic

Keep the following packages at their current version:
linux-restricted-modules-2.6.17-11-generic [Not Installed]

Score is -643

Accept this solution? [Y/n/q/?] 

```

I don't feel comfortable with accepting that... (the only solution aptitude proposes) I'm still a linux newb, but if I hit yes to that, I'm pretty sure I'll screw ubuntu up completely.

tried to manually get the linux image, and got the following message:
```

sudo apt-get install linux-image-2.6.17-11-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-2.6.17-11-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-image-2.6.17-11-generic has no installation candidate

```

Is there anyway to upgrade the kernel manually to 2.6.17-11 or to rollback to 2.6.17-10?

Any help appreciated.

---

### Post by mawdryn on 2007-02-13
Hmm.. It appears that not everything was downloaded/installed in the last set of updates.. New updates became available last night which after installing, brought all of the kernel versions back into line. I'm now happily running 2.6.17-11.

---

