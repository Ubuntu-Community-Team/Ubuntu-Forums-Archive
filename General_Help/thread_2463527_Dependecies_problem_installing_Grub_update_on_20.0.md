---
title: "Dependecies problem installing Grub update on 20.04.2"
date: 2021-06-13
forum: General Help
---

### Post by georgesgiralt on 2021-06-13
Hello,
Yesterday, I turned on a computer I've not used for a while.  This little machine runs the latest LTS version and is kept up to date.
So the first thing I did was to launch "Software updates" to get the latest packages.
Everything was fine except that the Grub update did not install and gave this messages :
```
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Transaction failed: Package dependencies cannot be resolved
 The following packages have unmet dependencies:

grub-efi-amd64-signed: Depends: grub2-common (>= 2.02~beta2-36ubuntu3.31) but 2.04-1ubuntu26.12 is to be installed
grub2-common: Depends: grub-common (= 2.04-1ubuntu26.12) but 2.04-1ubuntu26.12 is to be installed
              Depends: libc6 (>= 2.28) but 2.31-0ubuntu9.2 is to be installed
              Depends: libdevmapper1.02.1 (>= 2:1.02.36) but 2:1.02.167-1ubuntu1 is to be installed
              Depends: libefiboot1 (>= 37) but 37-2ubuntu2.2 is to be installed
              Depends: libefivar1 (>= 37) but 37-2ubuntu2.2 is to be installed
              Depends: liblzma5 (>= 5.1.1alpha+20120614) but 5.2.4-1ubuntu1 is to be installed
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Transaction failed: Package dependencies cannot be resolved
 The following packages have unmet dependencies:

grub-efi-amd64-signed: Depends: grub2-common (>= 2.02~beta2-36ubuntu3.31) but 2.04-1ubuntu26.12 is to be installed
grub2-common: Depends: grub-common (= 2.04-1ubuntu26.12) but 2.04-1ubuntu26.12 is to be installed
              Depends: libc6 (>= 2.28) but 2.31-0ubuntu9.2 is to be installed
              Depends: libdevmapper1.02.1 (>= 2:1.02.36) but 2:1.02.167-1ubuntu1 is to be installed
              Depends: libefiboot1 (>= 37) but 37-2ubuntu2.2 is to be installed
              Depends: libefivar1 (>= 37) but 37-2ubuntu2.2 is to be installed
              Depends: liblzma5 (>= 5.1.1alpha+20120614) but 5.2.4-1ubuntu1 is to be installed
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Transaction failed: Package dependencies cannot be resolved
 The following packages have unmet dependencies:

grub-efi-amd64-signed: Depends: grub2-common (>= 2.02~beta2-36ubuntu3.31) but 2.04-1ubuntu26.12 is to be installed
grub2-common: Depends: grub-common (= 2.04-1ubuntu26.12) but 2.04-1ubuntu26.12 is to be installed
              Depends: libc6 (>= 2.28) but 2.31-0ubuntu9.2 is to be installed
              Depends: libdevmapper1.02.1 (>= 2:1.02.36) but 2:1.02.167-1ubuntu1 is to be installed
              Depends: libefiboot1 (>= 37) but 37-2ubuntu2.2 is to be installed
              Depends: libefivar1 (>= 37) but 37-2ubuntu2.2 is to be installed
              Depends: liblzma5 (>= 5.1.1alpha+20120614) but 5.2.4-1ubuntu1 is to be installed

```
I checked on another computer with the same LTS version, this one kept up to date by running updates at least once every other day or every time the system demands it. 
I have all the very same libraries with the very same versions but the grub-efi-amd64-signed is version 1.167.2+2.04-1ubuntu44.2 which won't install on the offending machine. 
So how could I install the 3 packets (  grub-efi-amd64-signed, grub-common, grub2-common) without breaking anything or fixing the error ? 
Many thanks in advance for your help and answer !
Have a nice day and stay safe !

---

### Post by oldfred on 2021-06-13
It is wanting to install the signed versions.
Do you have UEFI Secure boot on?
Or did Windows or fwupd update UEFI and reset to defaults, turning Secure Boot back on?

Do you want Secure Boot?

---

### Post by georgesgiralt on 2021-06-13
> **oldfred said:**
> It is wanting to install the signed versions.
Do you have UEFI Secure boot on? 
Yes. Always have 
> 
Or did Windows or fwupd update UEFI and reset to defaults, turning Secure Boot back on?

Do you want Secure Boot?

Yes I do. This machine is used on a lot of foreign countries and use various untrusted networks on not so friendly locations. So every security setting I can think of are worth setting on.... 
Now, I have the following versions installed on the machine : 
```

ii  grub-common                                3.04-1ubuntu26.11                     amd64        GRand Unified Bootloader (common files)
ii  grub-efi-amd64                             2.04-1ubuntu44                        amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version)
ii  grub-efi-amd64-bin                         2.04-1ubuntu44                        amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 modules)
ii  grub-efi-amd64-signed                      1.167+2.04-1ubuntu44                  amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version, signed)
ii  grub2-common                               2.04-1ubuntu26.11                     amd64        GRand Unified Bootloader (common files for version 2)


```

---

### Post by oldfred on 2021-06-13
I might try these:
dpkg --configure -a
apt-get -f install

And then manually install each dependency.

---

### Post by georgesgiralt on 2021-06-13
The apt-get -f worries me....
On the laptop I use to post here I've got :
```

ii  grub-common                                   2.04-1ubuntu26.12                           amd64        GRand Unified Bootloader (common files)
ii  grub-efi-amd64-bin                            2.04-1ubuntu44.2                            amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 modules)
ii  grub-efi-amd64-signed                         1.167.2+2.04-1ubuntu44.2                    amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version, signed)
ii  grub-gfxpayload-lists                         0.7                                         amd64        GRUB gfxpayload blacklist
ii  grub-pc                                       2.04-1ubuntu26.12                           amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                   2.04-1ubuntu26.12                           amd64        GRand Unified Bootloader, version 2 (PC/BIOS modules)
ii  grub2-common                                  2.04-1ubuntu26.12                           amd64        GRand Unified Bootloader (common files for version 2)

```
And for libc6 for example : 
```

ii  libc6:amd64                                   2.31-0ubuntu9.2                             amd64        GNU C Library: Shared libraries
ii  libc6:i386                                    2.31-0ubuntu9.2                             i386         GNU C Library: Shared libraries
ii  libc6-dbg:amd64                               2.31-0ubuntu9.2                             amd64        GNU C Library: detached debugging symbols
ii  libc6-dev:amd64                               2.31-0ubuntu9.2                             amd64        GNU C Library: Development Libraries and Header Files

```
So I do not understand what' wrong on the offending machine...  How come I could update to the new version with the very same libc6 version ? 
I'm lost. 
The offending laptop has : 
```
i  libc6:amd64                                   2.31-0ubuntu9.2                             amd64        GNU C Library: Shared libraries
ii  libc6:i386                                    2.31-0ubuntu9.2                             i386         GNU C Library: Shared libraries
ii  libc6-dbg:amd64                               2.31-0ubuntu9.2                             amd64        GNU C Library: detached debugging symbols
ii  libc6-dev:amd64                               2.31-0ubuntu9.2                             amd64        GNU C Library: Development Libraries and Header Files

```
VEry strange.

---

### Post by grahammechanical on 2021-06-13
More than one person on this forum has posted about this particular problem. Someone, even posted a bug about it on Launchpad. This was about a month ago. It seems that the problem was fixed in a few days later.

[https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1928011](https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1928011)

> Because of the complexities of the changes to GRUB2 itself (over 100 patches to GRUB2 upstream) as well as the packaging changes above, we will first be publishing the GRUB2 updates via the SRU -proposed process to get more widespread testing before landing the updates in the updates or security pockets.

There have been a series of Grub security flaws for UEFI systems that need fixing. And the fix has been most complicated. It may be that all the pieces that make up the fix are not yet in place or not yet pushed out to all repositories and all machines.

[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass2021](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass2021)

Regards

---

### Post by georgesgiralt on 2021-06-13
OK. This make sense ! As I did not update every day on this machine, I've skipped some intermediate Grub updates and now caught back by the patrol ... I'll wait some days for the fix to show. As I'm not going abroad this time, it could be "safe".... 
Thank you all for your tremendous help !
Have a nice day !

---

