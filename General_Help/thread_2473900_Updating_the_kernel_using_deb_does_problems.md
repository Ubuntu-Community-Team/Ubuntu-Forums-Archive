---
title: "Updating the kernel using deb does problems ?"
date: 2022-04-17
forum: General Help
---

### Post by aug7744 on 2022-04-17
Hello.

I use Lubuntu (Ubuntu) 20.04.3 kernel 5.11.
In link below is possible download an AMD CPU optimized kernel 5.16.8.
[https://amdlinux.com](https://amdlinux.com)

If installing that optimized kernel is compatible with 20.04.3 ? Installing over does problems ?
Thanks for read.

---

### Post by QIII on 2022-04-17
Since the downloaded is from a third party site, note: "AMDLinux is a personal and independent Linux kernel optimization project", it would be hard to say what problems you might encounter.

I'd not do that.  Rather, I would backport from one of Canonical's repos for a more recent release of Ubuntu (might try kernel.ubuntu.com), or go directly to the official Linux kernel at kernel.org.

I would steer clear of downloading and installing someone's personal project.

Also note at the very bottom of the web page:  "**If you crash your machine during the installation it is solely your fault.**"

---

### Post by jeremy31 on 2022-04-17
If I remember correctly, the Ubuntu 5.11 kernel went EOL sometime in January and updates should have installed 5.13 by now

---

### Post by aug7744 on 2022-04-17
@QIII
Thanks for your reply.

I have entered kernel.ubuntu.com and not see there any link for download an kernel update deb file.

@jeremy31
Thanks for your comments.

Where to download an kernel update deb file ? Is available an kernel optimized for AMD CPUs ?
If have an kernel update deb file is possible simply use dpkg in that file installing over the current OS ?
If Ubuntu allow update using dpkg deb only need figure if the kernel origin is secure.

Not is an problem if first testing in an VirtualBox machine.

---

### Post by grahammechanical on 2022-04-17
> If I remember correctly, the Ubuntu 5.11 kernel went EOL sometime in January and updates should have installed 5.13 by now

Correct. The 20.04.4 point release with 5.13 kernel came out 24th February. So Software Updater should have made the transition.

I am wondering what the original poster wanted from a kernel optimized for AMD CPU's that the generic kernel does not provide.

Regards

Edit building the kernel for ourselves.

[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

---

### Post by ActionParsnip on 2022-04-18
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Impavidus on 2022-04-18
The regular upgrades you can install from the official repositories should have already upgraded your version string to 20.04.4 and kernel to 5.13.0-39. I suggest you first make sure the regular upgrades get installed before going further than that.

If you install a new kernel from a .deb file, it won't get automatic upgrades. From a PPA you will get those. Now, is there any reason to think that this alternative kernel is better for your computer than the generic kernel from the official repos?

---

### Post by #&amp;thj^% on 2022-04-18
Just to let you know this kernel was aimed at just a few AMD machines, IE:
```
Name            : linux-amd
Version         : 5.17.v.3-1
Description     : **_Linux kernel aimed at the latest AMD Ryzen CPU based hardware (ZNVER3/MZEN3)_**
Architecture    : x86_64
URL             : https://www.kernel.org/

```
After a few days of using it, I see very little difference (or none) between any current kernels from 5.13 and newer.
```
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB

```
I've yet to discover any meaningful reasons to risk a unknown kernel provider.
Also I did not use the .debs I compiled it from (with patches): [https://www.kernel.org/](https://www.kernel.org/)
I'm not* claiming there is no benefit from running it, I just haven't used it enough to discover thier claims (That it's any better than what we have now). BTW the current version is >>5.17.v.3-1
Note: It did not break anything hardware wise on my machine. Nor did I notice any significant improvements.
```
Depends On      : coreutils  linux-firmware  kmod  mkinitcpio>=0.7  lzop
Optional Deps   : crda: to set the correct wireless channels of your country [installed]
Required By     : None
Optional For    : None
Conflicts With  : None
Replaces        : None
Installed Size  : 144.41 MiB
Packager        : Unknown Packager

```
I seem to have been the only tester that did not sign off on it. (out of 6)
the jury is still out on this one.
EDIT: if you use hibernate, it does come out of that crisper.

---

### Post by ajgreeny on 2022-04-18
I wonder if it might be worth installing the package ***linux-generic-hwe*** which will pull in the ***5.13*** kernel series and all the headers etc, that are also needed for that kernel version.

If it does not help you can remove it and all the packages pulled in by it and go back to where you currently are, though the 5.11 series is now EOL so really is not secure to continue using.

---

### Post by aug7744 on 2022-04-18
Thanks for all replies and patience with me !
I am new in Linux since 2020 and not want return to previous OS.
For an long time always had anyone saying Linux is complex and etc.
In my little time using Linux simply I need say Linux is really complex and more time to configure than other OS ?
Not.
I can install an Linux Ubuntu distro configurating and installing all softwares in much less of half of time if trying to do the same action in other OS.
In others words ... is totally no sense Linux is more complex.
The only real detail for new users Linux is more hard to figure the root of one problem than other OS.

@grahammechanical
"I am wondering what the original poster wanted from a kernel optimized for AMD CPU's that the generic kernel does not provide."
Thanks for that reply !!! In others words that kernel optmized not will have an big gain in performance.

@Impavidus
Is possible install kernel 5.16 over 5.11 ? or only first is possible install version string to 20.04.4 and kernel 5.13 ?
Not problem if break automatic upgrades. I not want automatic upgrades.

@ActionParsnip

From link
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)
What is the more recent stable kernel ? 5.17.3 or the 5.17-rcX ?
I only need copy the deb files and run using dpkg -i *.deb ?

@1fallen
I want update kernel only because btrfs and dm-writecache.
I see problems when using dm-writecache in btrfs when happen an partial written.
Simply the partition metadata is damaged not being possible mount or any fix.
Perhaps new kernel modules have fixed that problem.
I use BTRFS because does high compression using zlib.
I not known if have another file system alternative with more high compression.

@ajgreeny
Simply only in /boot deleting config. initrd and system named related with the kernel update are removed all related with the new kernel update ?

In the link below look how if was used kernel from "https://kernel.ubuntu.com/~kernel-ppa/mainline/"

[https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline/](https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline/)

That link above is secure ?
I will install an test install in another disk and will try install that PPA installing kernel update.
After I reply the results.

---

### Post by #&amp;thj^% on 2022-04-18
> **aug7744 said:**
> 
[https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline/](https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline/)

That link above is secure ?
I will install an test install in another disk and will try install that PPA installing kernel update.
After I reply the results.
Well it comes with standard warning:
> Adding this PPA to your system

You can update your system with unsupported packages from this untrusted PPA by adding ppa:tuxinvader/lts-mainline to your system's Software Sources.

---

### Post by #&amp;thj^% on 2022-04-18
> **aug7744 said:**
> 

@1fallen
I want update kernel only because btrfs and dm-writecache.
**_I see problems when using dm-writecache in btrfs _**when happen an partial written.
Simply the partition metadata is damaged not being possible mount or any fix.




I just noticed this:  [problems when using dm-writecache in btrfs ]
"Disable the write cache on each drive by running "**hdparm -W0 /dev/sda**" against each drive on every boot.

Failure to perform this can result in massive and possibly irrecoverable corruption (especially in the case of encrypted filesystems). "

---

### Post by ajgreeny on 2022-04-18
> **aug7744 said:**
> Thanks for all replies and patience with me !
I am new in Linux since 2020 and not want return to previous OS.
For an long time always had anyone saying Linux is complex and etc.
In my little time using Linux simply I need say Linux is really complex and more time to configure than other OS ?
Not.
I can install an Linux Ubuntu distro configurating and installing all softwares in much less of half of time if trying to do the same action in other OS.
In others words ... is totally no sense Linux is more complex.
The only real detail for new users Linux is more hard to figure the root of one problem than other OS.


@ajgreeny
Simply only in /boot deleting config. initrd and system named related with the kernel update are removed all related with the new kernel update ?


[COLOR="#FF0000"]No, do not do that![/COLOR]
You should almost never delete anything directly from /boot but let the apt or dpkg systems do that for you after removing packages in the normal way, ie, either ***sudo apt remove***, or occasionally ***sudo dpkg purge***.

Manually deleting files from /boot will always risk leaving the package management system in a broken state and potentially unable to boot.

---

### Post by aug7744 on 2022-04-19
@1fallen
Thanks for the information about "hdparm -W0".

I have installed kernel 5.17.3 from PPA
[https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline/](https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline/)

@ajgreeny
"never delete anything directly from /boot but let the apt or dpkg systems do"
Thanks for that information.

I had created an /boot using 400 MB.
After installed the kernel update not had enough space to install nvidia driver.
How I had installed in an disk for testing I had removed files related with kernel 5.11 and was possible install nvidia driver, but was damaged the OS boot.
I not had another choice.
After was installed another OS and I had used the command below and was possible install nvidia driver.
sudo update-initramfs -d -k 5.11.0-27-generic

Now trying figure how remove only all possible files related with kernel 5.11.0-27.

---

### Post by ajgreeny on 2022-04-19
Assuming you have not corrupted the system already when deleting files from /boot you may find that running the command ```
sudo apt purge *5.11.0-27* -s
``` will tell you what would happen if you run the command a second time, omitting the -s (simulate) option.
It should purge all packages of version 5.11.0-27 including any linux-header, linux-modules and other related packages.

I can not help with the nvidia situation, never having used any nvidia hardware.

---

### Post by #&amp;thj^% on 2022-04-27
After Today's update on linux-amd.
Support Staff I'm also adding and quoting some from V1del

It enables gcc optimizations for CPU specifics. While this does sound cool in theory, the practice of the matter is that it often really doesn't help all that much. Architecture instructions and the like are built into the kernel anyway. There are some workloads where it might help, some where it likely doesn't matter.

As most "would I recommend the kernel" support threads this can't really be answered you have to do it and experience it and measure the differences (or believe in your placebo that it must be better)

It's unlikely that that minuscule improvement outweighs the amount of time you might waste for kernel compilation.
my guess here that the big daddy 32 cores or 64 threads per socket
256GB memory per socket amounting to 512GB in total gain the most improvement.
[https://lore.kernel.org/lkml/20220128052851.17162-1-bharata@amd.com/](https://lore.kernel.org/lkml/20220128052851.17162-1-bharata@amd.com/)

---

### Post by aug7744 on 2022-05-06
Thanks for all replies.

I have used Cubic for integrate kernel deb update files in Lubuntu 20.04.3 ISO.
Using kernel update from
[https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline/](https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline/)
Tested and all working correctly.
The OS was installed with kernel version from update deb.
I see btrfs improvements about recover damaged file system not possible in previous kernel 5.10.

Have an nice day !

---

### Post by ActionParsnip on 2022-05-07
If you have good backups then it means you aren't so reliant on recovering file systems

---

