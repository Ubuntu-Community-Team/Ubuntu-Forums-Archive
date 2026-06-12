---
title: "Current 16.04 LTS Kernel Version Confusion"
date: 2017-07-29
forum: General Help
---

### Post by rsteinmetz70112 on 2017-07-29
I just gone through updating several Ubuntu machines and I noticed they have a variety of kernel versions.

Some Have 4.4.0-86

Some have 4.8.0-XX

The one I'm writing this on had 4.10.0-27

If I understand the documentation the current version for 16.04.2 should be 4.8.0-XX

All of the machines are AMD64 although some of the installs are i386 or multiarch

---

### Post by vocx on 2017-07-29
> **rsteinmetz70112 said:**
> I just gone through updating several Ubuntu machines and I noticed they have a variety of kernel versions.

Some Have 4.4.0-86

Some have 4.8.0-XX

The one I'm writing this on had 4.10.0-27

If I understand the documentation the current version for 16.04.2 should be 4.8.0-XX

All of the machines are AMD64 although some of the installs are i386 or multiarch
The kernel for a normal Ubuntu installation is fixed during its lifetime. That is, if 16.04 is released with 4.4, it will always have that kernel, with some security patches, of course. This would result in some incremental numbers such as 4.4.0-72, 4.4.0-75, 4.4.0-80, etc.

The same thing with Ubuntu 16.10, it should have 4.8. Ubuntu 17.04 should have 4.10. So, when you upgrade from 16.04, to 16.10, and 17.04, the kernel will be upgraded, but otherwise it will not. These fixed kernels for a release are called the general availability (GA) kernels. If you are using a different kernel than the GA one, this was installed in a special way, perhaps manually compiled from source or otherwise.

Now, the Ubuntu 16.04 version is special in that starting from this release, they will have an option for the user to install a rolling release kernel. This is called the hardware enablement (HWE) kernel, which is a special way to get the latest (4.10) kernel instead of the original GA 4.4 kernel. So, maybe these computers that you are looking at are using this HWE kernel package.
See here [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
See here [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

What do you mean multiarch? There is no such thing, you cannot have multiple architectures running at the same time. It should be x86_64 (64 bit), or i386 (32-bit), or PPC. For all intents and purposes x86_64 and i386 is the same thing.

---

### Post by rsteinmetz70112 on 2017-07-29
> **vocx said:**
> https://wiki.ubuntu.com/Kernel/LTSEnablementStack[/URL]
See here [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
That may be what happened but the wiki page
[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)
seems to indicate point releases of 16.04 LTS have different kernel versions. All of my machines should be 16.04.2. The kernels on my machines are all identified as -generic and do have the hwe notation. They have generally been updated using the Software Updater or apt-get.

> What do you mean multiarch? There is no such thing, you cannot have multiple architectures running at the same time. It should be x86_64 (64 bit), or i386 (32-bit), or PPC. For all intents and purposes x86_64 and i386 is the same thing.
This wiki page on multuarch support in Ubuntu. [https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)

---

### Post by Kris_M on 2017-07-29
I am running 16.04.2 and system update recently gave me 4.10.0-28

---

### Post by vocx on 2017-07-29
> **rsteinmetz70112 said:**
> That may be what happened but the wiki page
[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)
seems to indicate point releases of 16.04 LTS have different kernel versions. All of my machines should be 16.04.2. The kernels on my machines are all identified as -generic and do have the hwe notation. They have generally been updated using the Software Updater or apt-get.

I think this idea of the HWE kernel is fairly new so it may be that some systems did not upgrade the same way, and also maybe the documentation is not completely correct. Maybe they forgot to update it. I feel that is a general roadmap, but it's not set in stone. It says there that the third point release 16.04.3 does not have a defined kernel yet. It is listed as to be defined (TBD). Maybe you got a 4.8 kernel, and it was already bumped to 4.10 in some systems, and not in others. This is basically a disclaimer "things may change in the future, beware".

Since I installed 16.04 a year ago I still have the original 4.4 kernel, and I haven't used the HWE versions. Personally, I don't feel like using a newer kernel if I don't really need it. I guess people who install the 4.8 or 4.10 kernels mostly get it because of needed support for their video or wireless cards. I don't really know if this is good or bad, but I recently read that the last few kernel versions have been getting a lot of commits, so maybe they do support a lot of new hardware. [http://www.omgubuntu.co.uk/2017/07/linux-kernel-4-12-was-a-very-big-release](http://www.omgubuntu.co.uk/2017/07/linux-kernel-4-12-was-a-very-big-release)

> 
This wiki page on multuarch support in Ubuntu. [https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)
Okay, I thought it was going to be something like this. Personally, I would call this system a x86_64 machine with 32-bit support. I mean, I guess most of your system is running the 64-bit versions of everything, including the kernel, and only some packages are 32-bit, or not? I don't think most people think of "multiarch" as a thing, except maybe for specialized cross-compiling, or supporting 32-bit only software.

---

### Post by rsteinmetz70112 on 2017-07-30
Another data point. Yesterday I did a fresh re-install on one machine using a recent AMD64 DVD from and recently downloaded iso. It installed a 4.8 kernel. This morning I did an upgrade using the Software Update. It downloaded and installed a 4.10 kernel.

I also see another thread where someon is asking more or less teh same question was recently moved to General Help.

---

### Post by efflandt on 2017-07-30
In the past, the kernel you ended up with (automatically) depended on the sub version of the Ubuntu version you originally installed. So if you installed original 14.04, you may have an older kernel than somewhere in the range of 14.04.1 though 14.04.5, even though all systems were updated and said they were currently 14.04.5. Although, you could manually change kernel version and then updates should follow that kernel series.

I don't have details if or how that may have changed in 16.04 because I initially had problems with 16.04 and skipped to 16.10.

---

### Post by rsteinmetz70112 on 2017-07-31
It does appear that something has changed in 16.04.2 LTS. All of my machines were originally installed as 16,04.1 with the 4.4 kernel. I never upgrade production machine until the .1 LTS version, in fact the Software Updater will not offer an in place upgrade until the .1 release of an LTS version.

It looks like if you install the 16.04.2 version you get the 4.8 kernel and it is upgraded to the 4.10 kernel. However if you install the 16.04.1 version you get the 4.4 kernel and it is not upgraded.

---

### Post by vocx on 2017-07-31
> **rsteinmetz70112 said:**
> It does appear that something has changed in 16.04.2 LTS. All of my machines were originally installed as 16,04.1 with the 4.4 kernel. I never upgrade production machine until the .1 LTS version, in fact the Software Updater will not offer an in place upgrade until the .1 release of an LTS version.

It looks like if you install the 16.04.2 version you get the 4.8 kernel and it is upgraded to the 4.10 kernel. However if you install the 16.04.1 version you get the 4.4 kernel and it is not upgraded.
Yes, I think this is right. My question now is, is this a problem for you? Or you just wanted certainty that this is the way it works? In my view, a 16.04 to 16.04.1 is not an "in place" upgrade, it's just the same system with all the previous updates since the original release. It's a significant milestone but it's not really a new system.

The wiki says that 16.04.1 has a 4.4 kernel. Starting with 16.04.2 the HWE kernel is installed by default on desktops, which will give you 4.8 and then 4.10. On servers, though, the 4.4. kernel is installed by default.
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

---

### Post by rsteinmetz70112 on 2017-07-31
> **vocx said:**
> Yes, I think this is right. My question now is, is this a problem for you? Or you just wanted certainty that this is the way it works? In my view, a 16.04 to 16.04.1 is not an "in place" upgrade, it's just the same system with all the previous updates since the original release. It's a significant milestone but it's not really a new system.

The wiki says that 16.04.1 has a 4.4 kernel. Starting with 16.04.2 the HWE kernel is installed by default on desktops, which will give you 4.8 and then 4.10. On servers, though, the 4.4. kernel is installed by default.
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

That looks like what I'm seeing. I don't have a problem I just didn't understand what I was seeing. I assume that If I install the HWE kernel on those systems running 4.4 then they would get periodic kernel version upgrades as well. I wonder if they will be more aggressive than the 16.04.2 upgrades.

Also I should have been clearer. All of my systems were previously 14.04 LTS and used the in place upgrade to go to 16.04.1 LTS.

Some of these have been in continuous service for a very long time with incremental upgrades in hardware and software. Somewhat like the farmer's old ax that that has had seven handles and three heads, but it's a good old ax.

---

### Post by Keith_Helms on 2017-08-01
As I understand it, 16.04.0 and 16.04.1 came with the linux-generic package and are fixed on the 4.4 kernel series.  16.04.2 and later refreshes come with the linux-generic-hwe-16.04 package which periodically moves to a newer kernel version.  It initially used the 4.8 kernel and recently updated to the 4.10 version.  A similar pair of packages is used for the xorg graphics with 16.04.2 and later.  The way the hwe process worked changed from 14.04 to 16.04.

You can read about it here:

[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

---

### Post by rsteinmetz70112 on 2017-08-01
Thanks for the link but If I understand this correctly it will change again in the next LTS release 

> This represents the path where HWE Stack users on Ubuntu 16.04 LTS will automatically upgrade to newer HWE Stacks until reaching the final 18.04 HWE Stack in Ubuntu 16.04 LTS. Users will then remain on this final 18.04 HWE Stack for the remaining supported life of the Ubuntu 16.04 LTS. If the user fully upgrades to Ubuntu 18.04 LTS, they will remain on the GA Kernel delivered in Ubuntu 18.04 LTS and will not continue rolling forward on HWE Stacks delivered for 18.04. This is the path that users will be put on if choosing to install the HWE Stack from the 16.04.2 or newer LTS point release. 

No mention of whether the 18.04.1 (.2) LTS will install a HWE kernel or if that will ever be done unless you specifically select the HWE kernel at some point.

Very confusing.

---

