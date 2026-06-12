---
title: "Trying to Upgrade but Aptitude &quot;Can't Find Any Solutions&quot;"
date: 2018-02-02
forum: General Help
---

### Post by Killing Vector on 2018-02-02
I'm trying to upgrade from Trusty to Xenical.

When I aptitude update, I get some rather strange messages:


```
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'libxapian-dev'
W: Unknown Multi-Arch type 'no' for package 'kwin'
...
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: You may want to run apt-get update to correct these problems
```


When I try to aptitude dist-upgrade, I get (pressing Y just leads to more or less the same thing):


```
open: 4847; closed: 17501; defer: 13; conflict: 16
No solution found within the allotted time.  Try harder? [Y/n]
```

After Googling for awhile, I read some advice that said to update apt first, but when I tried that, apt wanted to uninstall pretty much every single installed package on the system to resolve conflicts, which is clearly unacceptable.


I'm far from being knowledgeable about apt or even Ubuntu.  I fall under the class of people who want to use Linux without being an expert system admin.  However, I'm not completely helpless either.

Can someone please throw me some ideas to help upgrade my system?

Thanks!

---

### Post by TheFu on 2018-02-02
I'm in the middle of moving most of my 14.04 system to 16.04 too.
Did 2 yesterday - my main desktop and a server.  Server went fine.  Desktop I'm seeing only 1 issue - lost middle mouse click in the Window Manager.  Scroll works. Paste works (which uses the middle mouse button too!).

Doing another server now.  So far, so good.  It is a storage and media server.

My steps:
```
make a backup. Always make a know-you-can-restore backup before doing this stuff. ALWAYS!!!
sudo apt update  # a currently patched system is required before doing updates.
sudo apt dist-upgrade  # get the latest kernels too.
reboot, if needed. # libc or kernel updates mean a reboot is needed
login, if needed
sudo do-release-upgrade
```
Answer questions as you deem necessary based on your situation.  I modify many system config files and don't want those modifications lost over an upgrade.  Sometimes I want the newer package config files when my modifications aren't important anymore.

For example, I'll keep my version of ntp.conf and auto.master because I use NFS and run my own NTP server on the network with all my clients conf files pointing at MY NTP server.   I do other things while this process is going on. Coming up on an hour for the system today.  Not sure how fast it would be if I paid closer attention.

Aptitude used to be recommended by debian, but these days they recommend the simplified "apt" tool, which appears to be a nice front for apt-get.  Aptitude does come in handy when we need non-default packages which conflict with the most popular default tools for that task.  I was burned a few years ago when I was using mariaDB instead of mysql.  Another package had a specific dependency for mysql and removed mariaDB. That broke all my systems.  I think the packages are smarter today and don't require a specific DB anymore.

The system appears to have many manually loaded .deb files which are holding back many packages which have been updated.  You'll need to find those manually added packages and manually remove them, then update && upgrade && reboot && do-release-upgrade. Sorry, there isn't a magic wand that fixes everything.

Loading a newer OS will disable all 3rd party PPAs, so that the upgrade goes as clean for the base-OS as possible.  After the base-OS is updated, then you can go back and add those special programs/tools/packages back on again.   But it is best to solve these sorts of issues ASAP, during your weekly patching.  Any system that is on the internet, even as a client, needs to be patched weekly.  Basically, if you are installing .deb files directly, which is NOT recommended, then you have to manually handle all dependencies.  It is best to use the system versions for any programs. If that isn't new enough for your needs, use a PPA from a *reputable source*.  Only you can decide how reputable a PPA source might be.  The next best answer is to use a *snap* or flatpak. These are self-contained programs which bring all their dependencies with them.  Microsoft is deploying Skype as a "snap package" now.   Only after those other choices aren't possible would I go to a .deb file or downloading source code to be compiled and manually installed.  
The best reason I run Linux is the powerful package management and how all programs are integrated into it, not just the core OS files.

IMHO.

---

### Post by mc4man on 2018-02-02
Are you trying to use aptitude to do a release upgrade or using aptitude to update 14.04 before doing a release upgrade?
If the former, why??

---

### Post by Killing Vector on 2018-02-02
Thank you, TheFu.  That was helpful.

---

### Post by Killing Vector on 2018-02-02
> **mc4man said:**
> Are you trying to use aptitude to do a release upgrade or using aptitude to update 14.04 before doing a release upgrade?
If the former, why??

I wanted to upgrade the release, mostly because I'm using bleeding edge perl and python libraries (and things based on those libraries).

Also, I'm usually much to busy to tinker with my computer, but at this particular moment, I happen to have a lot of free time, so I figured I'd use some of it to learn a bit more about Ubuntu, i.e. how the upgrade process works.

---

### Post by TheFu on 2018-02-02
> **Killing Vector said:**
> I wanted to upgrade the release, mostly because I'm using bleeding edge perl and python libraries (and things based on those libraries).

Also, I'm usually much to busy to tinker with my computer, but at this particular moment, I happen to have a lot of free time, so I figured I'd use some of it to learn a bit more about Ubuntu, i.e. how the upgrade process works.

I'm a perl guy too.  **Never trust the system perl or system perl libraries.**

Use **perlbrew**.  This lets you have 20+ different perl environments, change between them as needed, and have different CPAN libraries for each. Perlbrew is a "best practice" for anyone doing perl that isn't specifically tied to exactly 1 distro and 1 release.

Python has something similar. I don't do python, maybe they call it pyenv? IDK.

---

