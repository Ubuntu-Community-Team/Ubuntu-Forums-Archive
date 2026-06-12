---
title: "NTFS-3G version number via Ubuntu repo vs No. at NTFS-3g.org"
date: 2008-05-27
forum: General Help
---

### Post by Herbivore on 2008-05-27
Searched on "ntfs-3g", and "version" and looked at each post before posting this message.

Can somebody please explain the version number of NTFS-3G available from the repository?

This number currently appears to be 1:1:1.913-2ubuntu1 which is quite different from the 1.2506 current stable version listed on the NTFS-3G Release History page.

This question was posted to NTFS-3g.org forums and received replies from Szaka, the lead developer who referred me to Ubuntu/Mint: [http://forum.ntfs-3g.org/viewtopic.php?p=3458#3458](http://forum.ntfs-3g.org/viewtopic.php?p=3458#3458)

Also copying this post to the Mint forum.

Really need NTFS-3G to be up-to-date!

Any assistance appreciated!

System: Ubuntu 7.1 Gutsy, Mint 4.0 Daryna, Kernel 2.6.22-14-generic, Gnome 2.20.1 on AMD 64 3200+, 2.0GB RAM

---

### Post by Nepherte on 2008-05-27
What does the output of the following command say?
```
ntfs-config --help
```

The output on hardy for me is:
```
bart@Athena:~$ ntfs-3g --help

**ntfs-3g 1.2216** external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2006-2008 Szabolcs Szakacsits
Copyright (C) 2005-2007 Yura Pakhuchiy

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro (read-only mount), force, remove_hiberfile, locale=,
          uid=, gid=, umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force

Ntfs-3g news, support and information:  http://ntfs-3g.org
```

Why would you need ntfs-config the be the latest version? I've never experienced any problem with repository version for gutsy and hardy.

---

### Post by Herbivore on 2008-05-27
Thanks, Nepherte. 

> What does the output of the following command say?

pampa1@pampa1:~$ ntfs-3g --help

ntfs-3g 1.913 - Third Generation NTFS Driver

Copyright (C) 2005-2006 Yura Pakhuchiy
Copyright (C) 2006-2007 Szabolcs Szakacsits

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro, force, locale=, uid=, gid=, umask=, fmask=, dmask=,
          streams_interface=. Please see details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force,locale=en_EN.UTF-8

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

> Why would you need ntfs-config the be the latest version? I've never experienced any problem with repository version for gutsy and hardy.

I've had mount problems and excessive CPU problems on external USB ntfs drive. When searching for answers it was suggested by the developer of NTFS-3G that one have the latest version of the driver. This seemed to be a reasonable suggestion -- not having the latest version of a software, especially a driver, would seem to set one up for difficulties otherwise avoidable -- but maybe it is not needed in this case. "If it ain't broke, don't fix it." But keeping software and drivers up-to-date doesn't seem to fall in the category of fixing. More like preventive strategy. 

But you're right. My current problem was caused by excessive fragmentation on the USB drive so I just copied the backup to a hard disk and reformated the USB and ran flyback again. NTFS-3G was no longer tasking most of the CPU.

The purpose of this post was to understand the version numbers and perhaps to find out why the current stable version of the driver is not in the repositories.

---

### Post by Nepherte on 2008-05-27
This is just for the record as your problem is already fixed.

In case you need a newer/latest version of a piece of software, you can remove your current installation:
```
sudo aptitude purge <packagename>
```
and download the latest source archive file from their site, unpack it and isntall it:
```
./configure
make
make install
```
Mostly you can find additional information on the site of the software developper about compiling it manually, as is the case for ntfs-3g:
[http://www.ntfs-3g.org/index.html#installation](http://www.ntfs-3g.org/index.html#installation)

---

### Post by Herbivore on 2008-05-28
> **Nepherte said:**
> This is just for the record as your problem is already fixed.

In case you need a newer/latest version of a piece of software, you can remove your current installation:
```
sudo aptitude purge <packagename>
```
and download the latest source archive file from their site, unpack it and isntall it:
```
./configure
make
make install
```
Mostly you can find additional information on the site of the software developper about compiling it manually, as is the case for ntfs-3g:
[http://www.ntfs-3g.org/index.html#installation](http://www.ntfs-3g.org/index.html#installation)

Thanks again. Compiling will be a step deeper for me, but perhaps it is time to give it a try.

Do you have any idea why repositories are not for updates, only security fixes (if i have understood from an answer at [www.linuxmint.com/forum/viewtopic.php?f=90&t=12875&p=80272&e=80272)?](www.linuxmint.com/forum/viewtopic.php?f=90&t=12875&p=80272&e=80272)?)

---

### Post by Zorael on 2008-05-28
Put simply, because that's the stance Ubuntu has taken. As a distro it's still "pretty close" to the bleeding edge, but sadly, you can't be super up-to-date *and* rock stable at the same time. Hence the opt-in backports.
> [SIZE="4"]What are Backports[/SIZE]
Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages stays constant for the entire 6 months. For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain at OpenOffice.org 2.0.x for the entire 6-month release cycle, even if a later version gets released during this time. The Ubuntu team may apply important security fixes to 2.0.x, but any new features or non-security bugfixes will not be made available.

This is where Ubuntu Backports comes in. The Backports team believes that the best update policy is a mix of Ubuntu's security-only policy AND providing new versions of some programs. Candidates for version updates are primarily desktop applications, such as your web browser, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system.

Backports is an official Ubuntu repository and maintained by knowledgeable Ubuntu developers who are often present on IRC and other communications media. But note that software in backports will not receive review or updates from the Ubuntu security team itself.

[SIZE="4"]-backports vs -proposed/-updates/-security[/SIZE]
A new user may be confused as to how the various official repositories that provides updates differ.

**-security** offers patches for security vulnerabilities in Ubuntu packages. They are managed by the Ubuntu Security Team and are designed to change the behavior of the package as little as possible -- in fact, the minimum required to resolve the security problem. As a result, they tend to be very low-risk to apply and all users are urged to apply security updates.

**-updates** offers patches for serious bugs in Ubuntu packaging that do not affect the security of the system. More directly, serious bugs are bugs that can directly cause loss of user data or represent a severe deviance from expected behavior. These updates are held up to similarly strict quality assurance as -security, in that the patches must be the minimum amount of change required to fix the bug. The fixes must be documented and verified by QA testers before they are accepted. These should also be low-risk to breakage and users are recommended to install them as a part of a regular update, or pick updates to bugs that affect them.

**-proposed** is the testing area for -updates. A number of people must give positive feedback on these packages before they are allowed into -updates. This repository is recommend to ONLY interested in helping to test updates and provide feedback. Since they are in effect testing updates, there is a higher chance of defective updates in this repository.

Full up to date information on update policies can be found at StableReleaseUpdates. The policies for main and universe differ, and can both be found at the mentioned page.

[SIZE="4"]Stability[/SIZE]
Backports candidates are tested by several Backports developers and community contributors before they are allowed to be placed in the repository. Backports packages are thus safer to use than the development distribution. At minimum the packages should be usable in a manner that the average Backports developer could test. However, given the nature of introducing newer versioned packages from a development distribution into a stable, released distribution, problems can arise. The most common side-effects would be a bug that escaped testing, or a new configuration file format (or other kind of incompatibility). If you have problems with a Backports package please report it in the Backports bugtracker and not the main Ubuntu one.

Due to the nature and purpose of Backports, it is not as "stable" as the previously mentioned update repositories, for a variety of reasons.

[list][*]Backports are designed to provide new features. These new features may be unfamiliar to users and require a period of re-learning to become familiar with their favorite application again.
[*]Backports may introduce differing configuration file options or behavior that may catch an administrator off guard. For this reason it's not encouraged to upgrade backports as a part of an automated procedure on high-stability production environments.
[*]Backports are newer software by definition, and newer software tends to be tested by fewer people. The risk for an uncaught bug is increased.[/list]

In assessing the "stability" of backports, it's important to define the term stability first. In terms of "the behavior I see today is the same as the behavior I'll see after applying a bunch of backports updates", Backports is fairly unstable. New apps introduced via backports may have significantly changed behavior or interfaces. In terms of "applying a backport will completely break my system", Backports is fairly stable. A great deal of work goes into testing backports and it's highly unlikely for a backport to be a severe regression from the version it replaces.

The user should judge for himself if Backports are appropriate for his purposes.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Herbivore on 2008-05-28
> **Zorael said:**
> Put simply, because that's the stance Ubuntu has taken. As a distro it's still "pretty close" to the bleeding edge, but sadly, you can't be super up-to-date *and* rock stable at the same time. Hence the opt-in backports.

A complete answer. Thank you for posting the exercpts from [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports). Now I see the logic.

---

