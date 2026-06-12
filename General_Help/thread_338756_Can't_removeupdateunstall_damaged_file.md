---
title: "Can't remove/update/unstall damaged file"
date: 2007-01-14
forum: General Help
---

### Post by ~LoKe on 2007-01-14
**EDIT:** Alright, I got it.  Had to edit /var/lib/dpkg/status and remove the entries for wpa_supplicant.

I've got this package, "wpasupplicant".  I didn't look it up, but I'm thinking it has to do with Wireless encryption?  I don't use wireless, but since it came up during my upgrade, I figured it had a reason to be there.  Well, after trying to get it, it spit out an error.

> loke@x04d:~$ sudo apt-get -f install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  beryl-settings-bindings libmysqlclient15-dev upstart-compat-sysv
  nvidia-kernel-common libssl-dev startup-tasks system-services upstart-logd
  upstart dpatch
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  wpasupplicant
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
12 not fully installed or removed.
Need to get 0B/621kB of archives.
After unpacking 389kB of additional disk space will be used.
(Reading database ... 110358 files and directories currently installed.)
Preparing to replace wpasupplicant 0.5.5-3v1ubuntu4 (using .../wpasupplicant_0.5.7+3v1ubuntu3_i386.deb) ...
Unpacking replacement wpasupplicant ...
dpkg: warning - old post-removal script returned error exit status 10
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 10
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried to dpkg -r, search for it and completely remove it in synaptic, remove it with aptitude, force it, delete the cached .deb via the command line **and it still doesn't work**.

Anyone have any ideas?

All help appreciated.

**EDIT:** There was a suggest package; kwlan, so I figured I'd install it, perhaps it would fix something.  Then I tried to remove wpasupplicant, and still it didn't go.  Now I tried to use aptitude to remove both:
> loke@x04d:~$ sudo aptitude remove kwlan wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  beryl-settings-bindings 
The following packages will be REMOVED:
  kwlan wpasupplicant 
0 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 1421kB will be freed.
Writing extended state information... Done
(Reading database ... 110358 files and directories currently installed.)
Removing kwlan ...
dpkg: error processing wpasupplicant (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 wpasupplicant
Aborted (core dumped)
I'm out of ideas.

---

### Post by mjpoetic on 2007-01-15
thanks!!  just ran into this problem

---

### Post by ~LoKe on 2007-01-15
> **mjpoetic said:**
> thanks!!  just ran into this problem

No problem! =]

---

