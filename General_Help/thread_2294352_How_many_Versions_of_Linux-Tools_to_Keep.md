---
title: "How many Versions of Linux-Tools to Keep?"
date: 2015-09-10
forum: General Help
---

### Post by BlueAZ on 2015-09-10
Hello,   When installing kernel updates, I learned that I have to clear out some of the old linux-image and linux-header versions to have enough space for new ones to install.  I was getting an error message, and found that answer in these Forums.  To do it, I use Synaptic Package Manager and search "Installed" for "linux-".   I'm using 14.04 till the next LTS version comes out, so quite a few had accumulated.  The current one is 3.13.0-63, I believe.  So I've been able to clear out all versions except the two most recent.  Works like a charm!

My question is this:  When reviewing these versions in Synaptic, I also see a lot of linux-tools and linux-utopic-tools versions.  Then today, I was notified to an update to 3.16.0-49 of linux-tools.   It's a bit confusing because it's not the same numbering system as the -image and -header versions.   So how many linux-tools versions do I need to keep?  Is it safe to get rid of earlier ones?  What is the difference between linux-tools and linux-utopic-tools?  

Looking forward to understanding this!

Thanks!

---

### Post by BlueAZ on 2015-09-28
Bump...  Does no one know?  Or is no one interested?
Thanks,  BlueAZ

---

### Post by sudodus on 2015-09-29
Maybe because we don't know. (It seems to be a meta-package. I don't know the details about what the packages in linux-tools are doing, how much space they are occupying, and if something would be broken if they are removed.)

Let us hope someone who knows will find this thread and reply :-)

---

### Post by BlueAZ on 2015-10-16
Bump again...  Doesn't anybody know about this??  I'd really like to know if I can remove some of these!
Thanks

---

### Post by efflandt on 2015-10-16
Maybe the reason some of us do not know is because we do not have any linux-tools version.```
efflandt@XPS-8100-1404:~$ uname -a
Linux XPS-8100-1404 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:08:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

efflandt@XPS-8100-1404:~$ dpkg-query -l linux-tools*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-============
un  linux-tools                 <none>             <none>             (no description available)
```

---

### Post by Bucky Ball on 2015-10-17
As above. Nope, I don't have 'linux-tools' any version installed. They're there in Synaptics, but none are installed. Running a minimal install with xfce4.

BTW, a search for 'linux-image' in Synaptics is also good for getting rid of the old kernels. Just remove the 'linux-image' number you don't want and that's it. The rest will also go. I generally run:

```
sudo apt-get autoremove 
```

in a terminal directly after also. :)

---

### Post by ajgreeny on 2015-10-17
Every time a new kernel arrives I always get rid of all unwanted packages including linux-image, linux-headers, etc etc of the old versions I no longer need.  I use synaptic for just about all my package management so search (name only) for the version numbers I want to remove, eg 3.13.0-61 and then remove all of the installed packages of that version.

Incidentally, I do not have any linux-tools packages installed either, and as far as I'm aware, never have.

---

### Post by vasa1 on 2015-10-17
On my 14.04 LTS fully updated, I see this:```
05:42 PM ~ $ apt-cache policy linux-tools-generic
linux-tools-generic:
  Installed: (none)
  Candidate: 3.13.0.65.71
  Version table:
     3.13.0.65.71 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     3.13.0.24.28 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
05:43 PM ~ $ 
```*apt-cache search linux-tools* comes up with several hits:```
5:43 PM ~ $ acse linux-tools
linux-tools-3.13.0-24 - Linux kernel version specific tools for version 3.13.0-24
linux-tools-3.13.0-24-generic - Linux kernel version specific tools for version 3.13.0-24
linux-tools-3.13.0-24-lowlatency - Linux kernel version specific tools for version 3.13.0-24
linux-tools-common - Linux kernel version specific tools for version 3.13.0
linux-tools-generic - Generic Linux kernel tools
linux-tools-generic-lts-saucy - Generic Linux kernel tools
linux-tools-generic-lts-trusty - Generic Linux kernel tools
linux-tools-lowlatency - lowlatency Linux kernel tools
linux-tools-lts-quantal - Linux kernel versioned Tools
linux-tools-lts-raring - Linux kernel versioned Tools
linux-tools-lts-saucy - Linux kernel versioned Tools
linux-tools-lts-trusty - Linux kernel versioned Tools
linux-tools-virtual - This package will always depend on the latest minimal generic kernel tools.
linux-tools-goldfish - Linux kernel tools for the goldfish kernel.
linux-goldfish-tools-3.4.0-3 - Linux kernel version specific tools for version 3.4.0-3
linux-tools-3.4.0-3-goldfish - Linux kernel version specific tools for version 3.4.0-3
linux-lts-utopic-tools-3.16.0-25 - Linux kernel version specific tools for version 3.16.0-25
linux-lts-utopic-tools-3.16.0-26 - Linux kernel version specific tools for version 3.16.0-26
linux-lts-utopic-tools-3.16.0-28 - Linux kernel version specific tools for version 3.16.0-28
linux-lts-utopic-tools-3.16.0-29 - Linux kernel version specific tools for version 3.16.0-29
linux-lts-utopic-tools-3.16.0-30 - Linux kernel version specific tools for version 3.16.0-30
linux-lts-utopic-tools-3.16.0-31 - Linux kernel version specific tools for version 3.16.0-31
linux-lts-utopic-tools-3.16.0-33 - Linux kernel version specific tools for version 3.16.0-33
linux-lts-utopic-tools-3.16.0-34 - Linux kernel version specific tools for version 3.16.0-34
linux-lts-utopic-tools-3.16.0-36 - Linux kernel version specific tools for version 3.16.0-36
linux-lts-utopic-tools-3.16.0-37 - Linux kernel version specific tools for version 3.16.0-37
linux-lts-utopic-tools-3.16.0-38 - Linux kernel version specific tools for version 3.16.0-38
linux-lts-utopic-tools-3.16.0-39 - Linux kernel version specific tools for version 3.16.0-39
linux-lts-utopic-tools-3.16.0-40 - Linux kernel version specific tools for version 3.16.0-40
linux-lts-utopic-tools-3.16.0-41 - Linux kernel version specific tools for version 3.16.0-41
linux-lts-utopic-tools-3.16.0-43 - Linux kernel version specific tools for version 3.16.0-43
linux-lts-utopic-tools-3.16.0-44 - Linux kernel version specific tools for version 3.16.0-44
linux-lts-utopic-tools-3.16.0-45 - Linux kernel version specific tools for version 3.16.0-45
linux-lts-utopic-tools-3.16.0-46 - Linux kernel version specific tools for version 3.16.0-46
linux-lts-utopic-tools-3.16.0-48 - Linux kernel version specific tools for version 3.16.0-48
linux-lts-utopic-tools-3.16.0-49 - Linux kernel version specific tools for version 3.16.0-49
linux-lts-utopic-tools-3.16.0-50 - Linux kernel version specific tools for version 3.16.0-50
linux-lts-vivid-tools-3.19.0-18 - Linux kernel version specific tools for version 3.19.0-18
linux-lts-vivid-tools-3.19.0-20 - Linux kernel version specific tools for version 3.19.0-20
linux-lts-vivid-tools-3.19.0-21 - Linux kernel version specific tools for version 3.19.0-21
linux-lts-vivid-tools-3.19.0-22 - Linux kernel version specific tools for version 3.19.0-22
linux-lts-vivid-tools-3.19.0-23 - Linux kernel version specific tools for version 3.19.0-23
linux-lts-vivid-tools-3.19.0-25 - Linux kernel version specific tools for version 3.19.0-25
linux-lts-vivid-tools-3.19.0-26 - Linux kernel version specific tools for version 3.19.0-26
linux-lts-vivid-tools-3.19.0-28 - Linux kernel version specific tools for version 3.19.0-28
linux-lts-vivid-tools-3.19.0-30 - Linux kernel version specific tools for version 3.19.0-30
linux-tools-3.13.0-27 - Linux kernel version specific tools for version 3.13.0-27
linux-tools-3.13.0-27-generic - Linux kernel version specific tools for version 3.13.0-27
linux-tools-3.13.0-27-lowlatency - Linux kernel version specific tools for version 3.13.0-27
linux-tools-3.13.0-29 - Linux kernel version specific tools for version 3.13.0-29
linux-tools-3.13.0-29-generic - Linux kernel version specific tools for version 3.13.0-29
linux-tools-3.13.0-29-lowlatency - Linux kernel version specific tools for version 3.13.0-29
linux-tools-3.13.0-30 - Linux kernel version specific tools for version 3.13.0-30
linux-tools-3.13.0-30-generic - Linux kernel version specific tools for version 3.13.0-30
linux-tools-3.13.0-30-lowlatency - Linux kernel version specific tools for version 3.13.0-30
linux-tools-3.13.0-32 - Linux kernel version specific tools for version 3.13.0-32
linux-tools-3.13.0-32-generic - Linux kernel version specific tools for version 3.13.0-32
linux-tools-3.13.0-32-lowlatency - Linux kernel version specific tools for version 3.13.0-32
linux-tools-3.13.0-33 - Linux kernel version specific tools for version 3.13.0-33
linux-tools-3.13.0-33-generic - Linux kernel version specific tools for version 3.13.0-33
linux-tools-3.13.0-33-lowlatency - Linux kernel version specific tools for version 3.13.0-33
linux-tools-3.13.0-34 - Linux kernel version specific tools for version 3.13.0-34
linux-tools-3.13.0-34-generic - Linux kernel version specific tools for version 3.13.0-34
linux-tools-3.13.0-34-lowlatency - Linux kernel version specific tools for version 3.13.0-34
linux-tools-3.13.0-35 - Linux kernel version specific tools for version 3.13.0-35
linux-tools-3.13.0-35-generic - Linux kernel version specific tools for version 3.13.0-35
linux-tools-3.13.0-35-lowlatency - Linux kernel version specific tools for version 3.13.0-35
linux-tools-3.13.0-36 - Linux kernel version specific tools for version 3.13.0-36
linux-tools-3.13.0-36-generic - Linux kernel version specific tools for version 3.13.0-36
linux-tools-3.13.0-36-lowlatency - Linux kernel version specific tools for version 3.13.0-36
linux-tools-3.13.0-37 - Linux kernel version specific tools for version 3.13.0-37
linux-tools-3.13.0-37-generic - Linux kernel version specific tools for version 3.13.0-37
linux-tools-3.13.0-37-lowlatency - Linux kernel version specific tools for version 3.13.0-37
linux-tools-3.13.0-39 - Linux kernel version specific tools for version 3.13.0-39
linux-tools-3.13.0-39-generic - Linux kernel version specific tools for version 3.13.0-39
linux-tools-3.13.0-39-lowlatency - Linux kernel version specific tools for version 3.13.0-39
linux-tools-3.13.0-40 - Linux kernel version specific tools for version 3.13.0-40
linux-tools-3.13.0-40-generic - Linux kernel version specific tools for version 3.13.0-40
linux-tools-3.13.0-40-lowlatency - Linux kernel version specific tools for version 3.13.0-40
linux-tools-3.13.0-41 - Linux kernel version specific tools for version 3.13.0-41
linux-tools-3.13.0-41-generic - Linux kernel version specific tools for version 3.13.0-41
linux-tools-3.13.0-41-lowlatency - Linux kernel version specific tools for version 3.13.0-41
linux-tools-3.13.0-43 - Linux kernel version specific tools for version 3.13.0-43
linux-tools-3.13.0-43-generic - Linux kernel version specific tools for version 3.13.0-43
linux-tools-3.13.0-43-lowlatency - Linux kernel version specific tools for version 3.13.0-43
linux-tools-3.13.0-44 - Linux kernel version specific tools for version 3.13.0-44
linux-tools-3.13.0-44-generic - Linux kernel version specific tools for version 3.13.0-44
linux-tools-3.13.0-44-lowlatency - Linux kernel version specific tools for version 3.13.0-44
linux-tools-3.13.0-45 - Linux kernel version specific tools for version 3.13.0-45
linux-tools-3.13.0-45-generic - Linux kernel version specific tools for version 3.13.0-45
linux-tools-3.13.0-45-lowlatency - Linux kernel version specific tools for version 3.13.0-45
linux-tools-3.13.0-46 - Linux kernel version specific tools for version 3.13.0-46
linux-tools-3.13.0-46-generic - Linux kernel version specific tools for version 3.13.0-46
linux-tools-3.13.0-46-lowlatency - Linux kernel version specific tools for version 3.13.0-46
linux-tools-3.13.0-48 - Linux kernel version specific tools for version 3.13.0-48
linux-tools-3.13.0-48-generic - Linux kernel version specific tools for version 3.13.0-48
linux-tools-3.13.0-48-lowlatency - Linux kernel version specific tools for version 3.13.0-48
linux-tools-3.13.0-49 - Linux kernel version specific tools for version 3.13.0-49
linux-tools-3.13.0-49-generic - Linux kernel version specific tools for version 3.13.0-49
linux-tools-3.13.0-49-lowlatency - Linux kernel version specific tools for version 3.13.0-49
linux-tools-3.13.0-51 - Linux kernel version specific tools for version 3.13.0-51
linux-tools-3.13.0-51-generic - Linux kernel version specific tools for version 3.13.0-51
linux-tools-3.13.0-51-lowlatency - Linux kernel version specific tools for version 3.13.0-51
linux-tools-3.13.0-52 - Linux kernel version specific tools for version 3.13.0-52
linux-tools-3.13.0-52-generic - Linux kernel version specific tools for version 3.13.0-52
linux-tools-3.13.0-52-lowlatency - Linux kernel version specific tools for version 3.13.0-52
linux-tools-3.13.0-53 - Linux kernel version specific tools for version 3.13.0-53
linux-tools-3.13.0-53-generic - Linux kernel version specific tools for version 3.13.0-53
linux-tools-3.13.0-53-lowlatency - Linux kernel version specific tools for version 3.13.0-53
linux-tools-3.13.0-54 - Linux kernel version specific tools for version 3.13.0-54
linux-tools-3.13.0-54-generic - Linux kernel version specific tools for version 3.13.0-54
linux-tools-3.13.0-54-lowlatency - Linux kernel version specific tools for version 3.13.0-54
linux-tools-3.13.0-55 - Linux kernel version specific tools for version 3.13.0-55
linux-tools-3.13.0-55-generic - Linux kernel version specific tools for version 3.13.0-55
linux-tools-3.13.0-55-lowlatency - Linux kernel version specific tools for version 3.13.0-55
linux-tools-3.13.0-57 - Linux kernel version specific tools for version 3.13.0-57
linux-tools-3.13.0-57-generic - Linux kernel version specific tools for version 3.13.0-57
linux-tools-3.13.0-57-lowlatency - Linux kernel version specific tools for version 3.13.0-57
linux-tools-3.13.0-58 - Linux kernel version specific tools for version 3.13.0-58
linux-tools-3.13.0-58-generic - Linux kernel version specific tools for version 3.13.0-58
linux-tools-3.13.0-58-lowlatency - Linux kernel version specific tools for version 3.13.0-58
linux-tools-3.13.0-59 - Linux kernel version specific tools for version 3.13.0-59
linux-tools-3.13.0-59-generic - Linux kernel version specific tools for version 3.13.0-59
linux-tools-3.13.0-59-lowlatency - Linux kernel version specific tools for version 3.13.0-59
linux-tools-3.13.0-61 - Linux kernel version specific tools for version 3.13.0-61
linux-tools-3.13.0-61-generic - Linux kernel version specific tools for version 3.13.0-61
linux-tools-3.13.0-61-lowlatency - Linux kernel version specific tools for version 3.13.0-61
linux-tools-3.13.0-62 - Linux kernel version specific tools for version 3.13.0-62
linux-tools-3.13.0-62-generic - Linux kernel version specific tools for version 3.13.0-62
linux-tools-3.13.0-62-lowlatency - Linux kernel version specific tools for version 3.13.0-62
linux-tools-3.13.0-63 - Linux kernel version specific tools for version 3.13.0-63
linux-tools-3.13.0-63-generic - Linux kernel version specific tools for version 3.13.0-63
linux-tools-3.13.0-63-lowlatency - Linux kernel version specific tools for version 3.13.0-63
linux-tools-3.13.0-65 - Linux kernel version specific tools for version 3.13.0-65
linux-tools-3.13.0-65-generic - Linux kernel version specific tools for version 3.13.0-65
linux-tools-3.13.0-65-lowlatency - Linux kernel version specific tools for version 3.13.0-65
linux-tools-3.16.0-25-generic - Linux kernel version specific tools for version 3.16.0-25
linux-tools-3.16.0-25-lowlatency - Linux kernel version specific tools for version 3.16.0-25
linux-tools-3.16.0-26-generic - Linux kernel version specific tools for version 3.16.0-26
linux-tools-3.16.0-26-lowlatency - Linux kernel version specific tools for version 3.16.0-26
linux-tools-3.16.0-28-generic - Linux kernel version specific tools for version 3.16.0-28
linux-tools-3.16.0-28-lowlatency - Linux kernel version specific tools for version 3.16.0-28
linux-tools-3.16.0-29-generic - Linux kernel version specific tools for version 3.16.0-29
linux-tools-3.16.0-29-lowlatency - Linux kernel version specific tools for version 3.16.0-29
linux-tools-3.16.0-30-generic - Linux kernel version specific tools for version 3.16.0-30
linux-tools-3.16.0-30-lowlatency - Linux kernel version specific tools for version 3.16.0-30
linux-tools-3.16.0-31-generic - Linux kernel version specific tools for version 3.16.0-31
linux-tools-3.16.0-31-lowlatency - Linux kernel version specific tools for version 3.16.0-31
linux-tools-3.16.0-33-generic - Linux kernel version specific tools for version 3.16.0-33
linux-tools-3.16.0-33-lowlatency - Linux kernel version specific tools for version 3.16.0-33
linux-tools-3.16.0-34-generic - Linux kernel version specific tools for version 3.16.0-34
linux-tools-3.16.0-34-lowlatency - Linux kernel version specific tools for version 3.16.0-34
linux-tools-3.16.0-36-generic - Linux kernel version specific tools for version 3.16.0-36
linux-tools-3.16.0-36-lowlatency - Linux kernel version specific tools for version 3.16.0-36
linux-tools-3.16.0-37-generic - Linux kernel version specific tools for version 3.16.0-37
linux-tools-3.16.0-37-lowlatency - Linux kernel version specific tools for version 3.16.0-37
linux-tools-3.16.0-38-generic - Linux kernel version specific tools for version 3.16.0-38
linux-tools-3.16.0-38-lowlatency - Linux kernel version specific tools for version 3.16.0-38
linux-tools-3.16.0-39-generic - Linux kernel version specific tools for version 3.16.0-39
linux-tools-3.16.0-39-lowlatency - Linux kernel version specific tools for version 3.16.0-39
linux-tools-3.16.0-40-generic - Linux kernel version specific tools for version 3.16.0-40
linux-tools-3.16.0-40-lowlatency - Linux kernel version specific tools for version 3.16.0-40
linux-tools-3.16.0-41-generic - Linux kernel version specific tools for version 3.16.0-41
linux-tools-3.16.0-41-lowlatency - Linux kernel version specific tools for version 3.16.0-41
linux-tools-3.16.0-43-generic - Linux kernel version specific tools for version 3.16.0-43
linux-tools-3.16.0-43-lowlatency - Linux kernel version specific tools for version 3.16.0-43
linux-tools-3.16.0-44-generic - Linux kernel version specific tools for version 3.16.0-44
linux-tools-3.16.0-44-lowlatency - Linux kernel version specific tools for version 3.16.0-44
linux-tools-3.16.0-45-generic - Linux kernel version specific tools for version 3.16.0-45
linux-tools-3.16.0-45-lowlatency - Linux kernel version specific tools for version 3.16.0-45
linux-tools-3.16.0-46-generic - Linux kernel version specific tools for version 3.16.0-46
linux-tools-3.16.0-46-lowlatency - Linux kernel version specific tools for version 3.16.0-46
linux-tools-3.16.0-48-generic - Linux kernel version specific tools for version 3.16.0-48
linux-tools-3.16.0-48-lowlatency - Linux kernel version specific tools for version 3.16.0-48
linux-tools-3.16.0-49-generic - Linux kernel version specific tools for version 3.16.0-49
linux-tools-3.16.0-49-lowlatency - Linux kernel version specific tools for version 3.16.0-49
linux-tools-3.16.0-50-generic - Linux kernel version specific tools for version 3.16.0-50
linux-tools-3.16.0-50-lowlatency - Linux kernel version specific tools for version 3.16.0-50
linux-tools-3.19.0-18-generic - Linux kernel version specific tools for version 3.19.0-18
linux-tools-3.19.0-18-lowlatency - Linux kernel version specific tools for version 3.19.0-18
linux-tools-3.19.0-20-generic - Linux kernel version specific tools for version 3.19.0-20
linux-tools-3.19.0-20-lowlatency - Linux kernel version specific tools for version 3.19.0-20
linux-tools-3.19.0-21-generic - Linux kernel version specific tools for version 3.19.0-21
linux-tools-3.19.0-21-lowlatency - Linux kernel version specific tools for version 3.19.0-21
linux-tools-3.19.0-22-generic - Linux kernel version specific tools for version 3.19.0-22
linux-tools-3.19.0-22-lowlatency - Linux kernel version specific tools for version 3.19.0-22
linux-tools-3.19.0-23-generic - Linux kernel version specific tools for version 3.19.0-23
linux-tools-3.19.0-23-lowlatency - Linux kernel version specific tools for version 3.19.0-23
linux-tools-3.19.0-25-generic - Linux kernel version specific tools for version 3.19.0-25
linux-tools-3.19.0-25-lowlatency - Linux kernel version specific tools for version 3.19.0-25
linux-tools-3.19.0-26-generic - Linux kernel version specific tools for version 3.19.0-26
linux-tools-3.19.0-26-lowlatency - Linux kernel version specific tools for version 3.19.0-26
linux-tools-3.19.0-28-generic - Linux kernel version specific tools for version 3.19.0-28
linux-tools-3.19.0-28-lowlatency - Linux kernel version specific tools for version 3.19.0-28
linux-tools-3.19.0-30-generic - Linux kernel version specific tools for version 3.19.0-30
linux-tools-3.19.0-30-lowlatency - Linux kernel version specific tools for version 3.19.0-30
linux-tools-generic-lts-utopic - Generic Linux kernel tools
linux-tools-generic-lts-vivid - Generic Linux kernel tools
linux-tools-lowlatency-lts-utopic - lowlatency Linux kernel tools
linux-tools-lowlatency-lts-vivid - lowlatency Linux kernel tools
linux-tools-lts-utopic - Linux kernel versioned Tools
linux-tools-virtual-lts-utopic - This package will always depend on the latest minimal generic kernel tools.
linux-tools-virtual-lts-vivid - This package will always depend on the latest minimal generic kernel tools.
05:45 PM ~ $ 
```

---

### Post by mc4man on 2015-10-17
If you use any of the linux tools then because the package is kernel version specific you only need the one for the kernel version you use the tools on.
If you want to have  that 'series' of linux-tools shown as updates then also install the metapackage, available metapackages shown in screen. Here I only use the lts-vivid kernel currently so have the corresponding linux-tools meta installed

---

### Post by Topsiho on 2015-10-17
I fully support BuckyBall's answer.
It works fine with my Ubuntu 14.04, though I have no version of Linux-tools installed.

If using the terminal is a problem: it's no more difficult then typing the command on whatever you want, and typing your password...

Topsiho

---

### Post by BlueAZ on 2015-10-17
OK, thanks for the input.  I guess I'm confused because all the linux-tools versions that come up on my system as Installed in Synaptic (see attached screenshot) were automatically installed during Ubuntu 14.04 updates.  I didn't choose them, that I know of.  I also get <none> if I run 
dpkg-query -l linux-tools

They just all show up in Synaptic, which is where I go to remove old kernels and headers.  As previously noted, their numbering isn't the same as the kernel versions.

[I hope I attached the png file right...]

Thanks!

---

### Post by LostFarmer on 2015-10-17
Just used Update Manager and it auto selected:  ( in Mint)
linux-headers-3.13.0-65
linux-headers-3.13.0-65-generic
linux-image-3.13.0-65-generic
linux-image-extra-3.13.0-65-generic
linux-lts-utopic-tools-3.16.0-50
linux-tools-3.13.0-65
linux-tools-3.13.0-65-generic
linux-tools-3.13.0-50-generic
linux-tools-common


Description for linux-tools-3.13.0-65-generic

This package provides the architecture dependant parts for kernel
version locked tools (such as perf and x86_energy_perf_policy) for
version 3.13.0-65 on
64 bit x86.

---

### Post by Bucky Ball on 2015-10-17
*Thread moved to **MINT**.*

Just clicked you are using Mint.

* Update: And moved back to General Help due to public demand (and mod error). :)

---

### Post by mc4man on 2015-10-18
> **BlueAZ said:**
> OK, thanks for the input.  I guess I'm confused because all the linux-tools versions that come up on my system as Installed in Synaptic (see attached screenshot) were automatically installed during Ubuntu 14.04 updates.  I didn't choose them, that I know of.  I also get <none> if I run 
dpkg-query -l linux-tools

They just all show up in Synaptic, which is where I go to remove old kernels and headers.  As previously noted, their numbering isn't the same as the kernel versions.

[I hope I attached the png file right...]

Thanks!
You can just remove them all if not using any of the tools.
(cpupower, perf, turbostat, ect.

If using a tool(s)  then remove all & install  the metapackage for whichever base kernel - so - 
for 3.13.x - linux-tools-generic
for 3.16.x - linux-tools-generic-lts-utopic
for 3.19.x - linux-tools-generic-lts-vivid

---

### Post by mc4man on 2015-10-18
> **Bucky Ball said:**
> *Thread moved to **MINT**.*

Just clicked you are using Mint.
Not mint specific & the OP didn't indicate mint anyway

---

### Post by Topsiho on 2015-10-18
The details about the OP mention that he or she is using Ubuntu 14.04 Trusty Tahr. So moving the topic to Mint is not correct. The topic should be moved back.

Topsiho

---

### Post by Bucky Ball on 2015-10-18
My mistake. Mistook LostFarmer, who is using Mint, for the OP. Moved back.

---

### Post by BlueAZ on 2016-02-17
Thanks for more responses!  My answer to Bucky Ball is that I have used

Sudo apt-get autoremove

but it doesn't actually remove old kernels & tools.

My list of Linux-Tools was long, like another poster's.  I've been experimenting with removing older ones, and it seems to work just fine.  At least it causes no problems for me.  So I'll mark this thread Solved.

I've started a thread in 16.04 Development to suggest that this kind of clean-up be included somehow automatically with user-options in the software updater.

---

