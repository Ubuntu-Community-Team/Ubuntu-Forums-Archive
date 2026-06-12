---
title: "help with deinstalling a very very broken package"
date: 2007-06-02
forum: General Help
---

### Post by skullmunky on 2007-06-02
i have a half-installed package that's preventing synaptic from running at all - i get an internal error (1).  adept will still run, but can't remove the offending package; i also can't kill it with dpkg even with --force options.  it's a bad, bad package.  help!  

using feisty i386, tried to install Maya 8.5.  since maya only comes as RPM's, converted to deb's with alien, tried to install.   got all kinds of errors, and i ended up simply turning the rpm into a .tgz and unpacking, since basically the entire install just goes into /usr/autodesk/maya.  works great.  

but: in the process, i have a half-installed package of awcommon.  here are some of the errors:

sudo dpkg -i awcommon_10.80-14_i386.deb

Unpacking replacement awcommon ...
/usr/bin/test: invalid integer `upgrade'
exit: 26: Illegal number: -0
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/usr/bin/test: invalid integer `failed-upgrade'
exit: 26: Illegal number: -0
dpkg: error processing awcommon_10.80-14_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
/usr/bin/test: invalid integer `abort-upgrade'
exit: 26: Illegal number: -0
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon_10.80-14_i386.deb



dpkg-query -l awcommon

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                   Version                                Description
+++-======================================-======================================-============================================================================================
iHR awcommon                               10.80-14                               AWCommon Linux 10.80 For Intel IA32


sudo dpkg --remove --force-remove-reinstreq awcommon


dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 170701 files and directories currently installed.)
Removing awcommon ...
/usr/bin/test: invalid integer `remove'
exit: 26: Illegal number: -0
dpkg: error processing awcommon (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon


all this package contains is a few license-manager tools stored in /usr/aw/COM

i'm happy to get rid of it, but how?  it seems like a catch-22: i can't remove it until i install, but i can't install it because it's a bad package in the first place!  is there a way i can just edit the package list by hand and make apt forget about it?

---

### Post by skullmunky on 2007-06-02
oops, answering my own post.  maybe it'll help others though.

in /var/lib/dpkg, i removed all mention of awcommon from 'available' and 'status'
in /var/lib/dpkg/info, removed awcommon.* (the info files for the package)

sudo apt-get update

now synaptic works again.  hoorah!

---

### Post by flawedprefect on 2007-06-08
> **skullmunky said:**
> oops, answering my own post.  maybe it'll help others though.

in /var/lib/dpkg, i removed all mention of awcommon from 'available' and 'status'
in /var/lib/dpkg/info, removed awcommon.* (the info files for the package)

sudo apt-get update

now synaptic works again.  hoorah!

Thanks for this. Was having exactly the same problem. Odd thing is - my copy of Maya 8.5 works fine. (Well... except for some render issues, but they are unrelated to this problem.)

---

### Post by apping on 2008-03-28
Thanks a loooooooooooooooooooooooot!

---

