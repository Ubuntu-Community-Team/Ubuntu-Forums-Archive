---
title: "How to use 17.10 Kernel in 16.04.3"
date: 2017-10-28
forum: General Help
---

### Post by kerrygee on 2017-10-28
Hi,

is there any way to install the 17.10 kernel (4.13x) on a 16.04.3 system, except downloading the Kernel Mainline Build .DEB files and install them manually?
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

I am looking for some way to switch my entire 16.04.3 systems kernel basis to the basis of the new 17.10 system, including the benefits of being able to update it automatically on a new release.

thanks in advance

K.

---

### Post by ian-weisser on 2017-10-28
See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by kerrygee on 2017-10-29
> **ian-weisser said:**
> See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Thanks for the reply. Actually i cant find any specific information how to switch right now, but AFAIU, the 16.04.4 will support it (at least the kernel used in 17.10) by design with its release. But how can i switch my current system to the 17.10 kernel by the usage of the 17.10 repositories?

---

### Post by ian-weisser on 2017-10-29
You cannot do so safely, unless you have lots of experience customizing and troubleshooting apt.
Mixing packages from different releases is a great way to break your system quite horribly.
The crux of the problem is that you have no easy way to prevent apt from pulling in hundreds of other new (incompatible) packages from the same 17.10 repository.

You are attempting to do something that the designers of Ubuntu did not envision:
The whole point of LTS is software stability (no changes)...which happens by staying on the provided path. If you don't want to be on that provided path, then perhaps LTS is the wrong product for you.

---

### Post by kerrygee on 2017-10-29
> **ian-weisser said:**
> You cannot do so safely, unless you have lots of experience customizing and troubleshooting apt.
Mixing packages from different releases is a great way to break your system quite horribly.
The crux of the problem is that you have no easy way to prevent apt from pulling in hundreds of other new (incompatible) packages from the same 17.10 repository.

You are attempting to do something that the designers of Ubuntu did not envision:
The whole point of LTS is software stability (no changes)...which happens by staying on the provided path. If you don't want to be on that provided path, then perhaps LTS is the wrong product for you.

Thank you for the detailed explanation. This sounds very logical. I guess, ill stay on the manual MainlineKernel installation method.

---

### Post by Impavidus on 2017-10-29
Unless you've got some very recent hardware, there's rarely a reason to upgrade your kernel from 4.10 to 4.13. Do you have a very good reason to want that upgrade anyway, and want it now? The 4.13 kernel will come with 16.04.4 in January, or use Ubuntu 17.10. It's not so well polished though, and you have to upgrade to 18.04 by June, but you probably want that anyway.

---

### Post by mc4man on 2017-10-29
This page should tell you & it's reasonably  safe. Plus if using prop drivers like nvidia they'll work fine.
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
You're looking for the section "hwe-16.04-edge"

Using it here, currently on one install ( from proposed repo - 
uname -a
Linux doug-Lenovo-IdeaPad-Y510P 4.13.0-16-generic #19~16.04.3-Ubuntu SMP

On another it's still at  (not using proposed
$ uname -a
Linux doug-Lenovo-IdeaPad-Y510P 4.11.0-14-generic #20~16.04.1-Ubuntu SMP

The package name to install for most users is
linux-generic-hwe-16.04-edge

(- unless looking for low latency then - 
linux-lowlatency-hwe-16.04-edge

---

### Post by kerrygee on 2017-10-30
> **mc4man said:**
> This page should tell you & it's reasonably  safe. Plus if using prop drivers like nvidia they'll work fine.
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
You're looking for the section "hwe-16.04-edge"

Using it here, currently on one install ( from proposed repo - 
uname -a
Linux doug-Lenovo-IdeaPad-Y510P 4.13.0-16-generic #19~16.04.3-Ubuntu SMP

On another it's still at  (not using proposed
$ uname -a
Linux doug-Lenovo-IdeaPad-Y510P 4.11.0-14-generic #20~16.04.1-Ubuntu SMP

The package name to install for most users is
linux-generic-hwe-16.04-edge

(- unless looking for low latency then - 
linux-lowlatency-hwe-16.04-edge

Hi, 

thank you all for the answers.

linux-generic-hwe-16.04-edge defaults on my system to 4.11.0-14-generic and not 4.13x

---

### Post by mc4man on 2017-10-30
> **kerrygee said:**
> Hi, 

thank you all for the answers.

linux-generic-hwe-16.04-edge defaults on my system to 4.11.0-14-generic and not 4.13x
As I mentioned the 4.13.x kernel is still in xenial -proposed so to get _now_ you'd need to enable the -proposed repo in your sources.

General best practice with -proposed after release is to enable, pick & choose, then disable (but remember what you used it for...
or enable & leave enabled but pay attention to what is being updated..

It's not always guaranteed that all proposed packages are promoted to main repos, in the case of the kernel this isn't a real issue but could cause some minor hiccups down the road if one just blindly updates all from -proposed.

Here I use synaptic for all updating, allows one to specify plus keeps an easy to read history of all activity.

---

### Post by kerrygee on 2017-10-30
> **mc4man said:**
> As I mentioned the 4.13.x kernel is still in xenial -proposed so to get _now_ you'd need to enable the -proposed repo in your sources.

General best practice with -proposed after release is to enable, pick & choose, then disable (but remember what you used it for...
or enable & leave enabled but pay attention to what is being updated..

It's not always guaranteed that all proposed packages are promoted to main repos, in the case of the kernel this isn't a real issue but could cause some minor hiccups down the road if one just blindly updates all from -proposed.

Here I use synaptic for all updating, allows one to specify plus keeps an easy to read history of all activity.

Ok, thanks. This was also very helpful: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

Also shows how to limit the installation/update of specific packages

---

