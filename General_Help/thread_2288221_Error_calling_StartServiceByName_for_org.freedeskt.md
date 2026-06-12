---
title: "Error calling StartServiceByName for org.freedesktop.PolicyKit1: Timeout was reached"
date: 2015-07-25
forum: General Help
---

### Post by edarchis on 2015-07-25
My server running 15.04  suddenly starting spitting the error in the title:

```

root@h:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 grub-pc : Depends: grub-common (= 2.02~beta2-22ubuntu1.1)
 grub-pc-bin : Depends: grub-common (= 2.02~beta2-22ubuntu1.1)
 grub2-common : Depends: grub-common (= 2.02~beta2-22ubuntu1.1)
E: Unmet dependencies. Try using -f.


root@h:~# apt-get install grub-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
Recommended packages:
  os-prober
The following packages will be upgraded:
  grub-common
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
206 not fully installed or removed.
Need to get 0 B/1,698 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 59618 files and directories currently installed.)
Preparing to unpack .../grub-common_2.02~beta2-22ubuntu1.1_amd64.deb ...
Error getting authority: Error initializing authority: Error calling StartServiceByName for org.freedesktop.PolicyKit1: Timeout was reached (g-io-error-quark, 24)
Failed to execute operation: Connection timed out

```

I have no idea why grub-common suddenly disappeared.
I have seen some bug reports suggesting to purge policykit-1 and then reinstalling it but it won't let me until I fix the missing depencies first resulting in the above error.

Any idea how I can get out of this mess ?

---

