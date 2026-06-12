---
title: "How to scan for packages that didn't install properly?"
date: 2019-03-14
forum: General Help
---

### Post by &amp;KyT$0P# on 2019-03-14
Running Xubuntu 18.04 64-bit.  Today I ran Software Updater and it "went rogue" and tried to install a bunch of 32-bit packages that were not listed in the list of updates, and that I neither need nor want.  This seemed so wrong that I decided to interrupt it.  But unfortunately the downloading stage went by too quickly for me to see what was happening and cancel it before installing started.  Software Updater didn't respond to a Ctrl+C in the terminal part, so I just closed it.

I tried to clean up the mess as follows.  First purge the 32-bit packages -
```
sudo apt-get purge $(dpkg-query -W -f '${binary:Package}\n' | grep -P ':i386$')
```

Then I re-ran Software Updater.  It listed one update, which I installed.  This time it didn't try to install 32-bit packages.

Somewhere in there I also ran this -
```
sudo dpkg --configure -a
```
That didn't seem to do anything.

But even after all that, I was still concerned that the updates might not have been installed correctly, so I reinstalled them through command line -
```
sudo apt-get --reinstall install libsystemd0:amd64 udev:amd64 libudev1:amd64 systemd-sysv:amd64 libpam-systemd:amd64 systemd:amd64 libnss-systemd:amd64 systemd-sysv:amd64
```

Things seem OK now, but I'd like to check to make sure.  How do I scan my system for packages that aren't installed properly?

---

### Post by Doug S on 2019-03-14
I use grep and filter by any lines that are not normal:

```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]dpkg -l | grep -v "^ii"[/COLOR]
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                                    Architecture Description
+++-=========================================-==========================================-============-===============================================================================
rc  kdump-tools                               1:1.6.3-2~16.04.1                          amd64        scripts and tools for automating kdump (Linux crash dumps)
rc  libpth20:amd64                            2.0.7-20                                   amd64        GNU Portable Threads
pi  linux-base                                4.5ubuntu1~16.04.1                         all          Linux image base package
[COLOR="#FF0000"]iU  linux-headers-5.0.0-999-lowlatency        5.0.0-999.201903132203                     amd64        Linux kernel headers for version 5.0.0 on 64 bit x86 SMP[/COLOR]
rc  php7.0-gd                                 7.0.4-7ubuntu2.1                           amd64        GD module for PHP
rc  uvtool                                    0~bzr99-0ubuntu1                           all          Library and tools for using Ubuntu Cloud images
```And observe, that I have some removed but configured packages, and a problem with a kernel

---

### Post by &amp;KyT$0P# on 2019-03-14
> **Doug S said:**
> I use grep and filter by any lines that are not normal:

```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]dpkg -l | grep -v "^ii"[/COLOR]
```

Thanks.  I only get this -
```
$ dpkg -l | grep -v '^ii'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                    Version                                   Architecture Description
+++-=======================================-=========================================-============-===============================================================================

```

I also ran
```
sudo debsums -ac
```
and this only shows files I deliberately modified, so I guess nothing was *unpacked* incorrectly.

So is it safe to conclude I'm good?

---

### Post by Doug S on 2019-03-14
> **halogen2 said:**
> So is it safe to conclude I'm good?Yes, I think so.

---

### Post by &amp;KyT$0P# on 2019-03-14
Cool :KS

Based on your answers, I did some man page reading, and tweaked the command to -
```
dpkg-query -l | grep -P -v '^ii '
```

Thanks again for your help! :D

---

