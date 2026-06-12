---
title: "unmet dependencies : linux-image-3.16.0-48-generic (55 and utopic)"
date: 2016-07-02
forum: General Help
---

### Post by sunil-choudhary on 2016-07-02
My Machine is on UBuntu 14.04 
tech@marg:~$ uname -a
Linux marg 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


CUrrently giving issues 
tech@marg:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.16.0-48-generic : Depends: linux-image-3.16.0-48-generic but it is not installed
 linux-image-extra-3.16.0-55-generic : Depends: linux-image-3.16.0-55-generic but it is not installed
 linux-image-extra-3.16.0-76-generic : Depends: linux-image-3.16.0-76-generic but it is not installed
 linux-image-generic-lts-utopic : Depends: linux-image-3.16.0-76-generic but it is not installed
E: Unmet dependencies. Try using -f.
tech@marg:~$ uname -a


Tried solving them using upgrade but not possible...
Basically I am hitting this as I am trying to install NPM.

Please help. 

thx
Sunil

---

### Post by sudodus on 2016-07-02
The utopic kernel series 3.16 is no longer supported. The original 14.04 LTS kernel, the trusty series 3.13 has LTS (long time support) until April 2019.

I suggest that you try one of the following:

- to install the current kernel of the 3.13 series (the one with the highest version number available) and reboot into that kernel. If it works, you should be able to remove the 3.16 kernels.

- to upgrade the hardware enablement stack to 14.04.4 (wily) or wait maybe 3 weeks for 14.04.5 LTS (xenial) according to this link (more risky, so back up your system before you start)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Impavidus on 2016-07-02
I thought that the Utopic, Vivid and Wily kernel series on Trusty would all be supported until the release of 14.04.5...


Anyway, what was the output when you ran```
sudo apt-get -f install
```as suggested? Without fixing the package manager, you can't upgrade to any kernel.

---

### Post by sudodus on 2016-07-02
> **Impavidus said:**
> I thought that the Utopic, Vivid and Wily kernel series on Trusty would all be supported until the release of 14.04.5...


Anyway, what was the output when you ran```
sudo apt-get -f install
```as suggested? Without fixing the package manager, you can't upgrade to any kernel.

My bad. Impavidus is right. Utopic has passed end of life, but its kernel series is supported as part of Trusty (as we can see in the link I provided).

But it is still worthwhile to test another kernel series.

---

### Post by sudodus on 2016-07-02
Oldfred's command list for cleaning and repairing
 
```
#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
``` 

Added zika's tip for problems with hash sum mismatch

```
sudo rm /var/lib/apt/lists/*
sudo apt-get update
```

# added 2F4U's tips for Package Manager & Update Manager problems

Does executing these commands help?

```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

This will rebuild the cache.

If it doesn't help, this forum post has additional suggestions:

[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

---

