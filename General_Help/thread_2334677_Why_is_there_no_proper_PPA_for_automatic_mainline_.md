---
title: "Why is there no proper PPA for automatic mainline kernel updates?"
date: 2016-08-21
forum: General Help
---

### Post by nw9165-3201 on 2016-08-21
Hi,

yes, I realize there is a mainline kernel "PPA":

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

But why isn't it possible to add this "PPA" just like any other PPA and get automatic updates through the regular software updates?

Regards

---

### Post by banceu_sergiu_ione on 2016-08-21
Hello
If you would had read the[ Introduction]("https://wiki.ubuntu.com/Kernel/MainlineBuilds"), at end of it it say: " These kernels are not supported and are not appropriate for production use "

You already get automatic updates of supported kernel via software updater.

---

### Post by nw9165-3201 on 2016-08-21
> **banceu_sergiu_ione said:**
> Hello
If you would had read the[ Introduction]("https://wiki.ubuntu.com/Kernel/MainlineBuilds"), at end of it it say: " These kernels are not supported and are not appropriate for production use "

Just because it says they are not supported, doesn't mean they can not be used.

Also, why is this even called a PPA, if it is not a proper PPA?

> **banceu_sergiu_ione said:**
> You already get automatic updates of supported kernel via software updater.

No, I do not. These are just security updates. But I want the latest kernels. I get automatic upgrades for the graphic drivers via the Oibaf PPA for example. So, I also want automatic updates for the latest kernels.

---

### Post by banceu_sergiu_ione on 2016-08-21
That is not a ppa, is a wiki.

Check your kernel version with :
```
 uname -a 
```

and post the output.

---

### Post by nw9165-3201 on 2016-08-21
> **banceu_sergiu_ione said:**
> That is not a ppa, is a wiki.

You don't say :rolleyes:?

I am referring to the "kernel-ppa" in:

 [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

> **banceu_sergiu_ione said:**
> Check your kernel version with :
```
 uname -a 
```

and post the output.

And then? I am currently being booted into the Xenial (4.4) kernel:

```
uname -a
Linux pc 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

 Yes, I realize that -34 stands for the update number. But that is just a security or bug fix update, not a real update to a new kernel. Xenial stays on kernel 4.4 over the entire life of Xenial.

Yes, I know it's possible to upgrade to the Ubuntu+1 kernel via the LTS enablement stacks. But it takes months for them to arrive. And when they arrive, they are already outdated.

What's so hard to understand about the fact that someone wants to stay up-to-date on the kernel?

I'm not even interested in release candidate kernels. Just normal kernel releases.

It definitely would be nice if that would be possible via normal and automatic software updates.

---

### Post by banceu_sergiu_ione on 2016-08-21
Via software updates will get only what is known to be a stable release for all.

The upstream kernels are most a work in progress/test and are use for debugging. And I quote from: The mainline kernel builds are produced for debugging purposes and therefore come with no support.  Use them at your own risk.
If you scroll a bit down you can see how to manually install. Or you can search for same howto install new kernel. I think you can find something for 4.7 or 4.8 kernel.

---

### Post by grahammechanical on 2016-08-21
> It definitely would be nice if that would be possible via normal and automatic software updates.

For you it would be nice because that is what you want. But for millions of other people it would not be nice because it would risk breaking the OS for many people. 

You are the kind of person who should be using the development version of Ubuntu. Soon the development version of 16.10 (yakkety yak) will be getting Linux kernel 4.6 and it seems likely that 16.10 will have Linux kernel 4.8 by release day. And all by means of doing normal updates every day.

[https://wiki.ubuntu.com/KernelTeam/Newsletter](https://wiki.ubuntu.com/KernelTeam/Newsletter)

Oh, by the way, this is not accurate

> Xenial stays on kernel 4.4 over the entire life of Xenial.

By the 16.04.2 release Xenial will have kernel 4.8. True existing users of 16.04 will have to upgrade to the yakkety hardware enablement stack. But the 16.04 ISO image will install kernel 4.8 at that time.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)




Regards

---

### Post by nw9165-3201 on 2016-08-22
> **banceu_sergiu_ione said:**
> If you scroll a bit down you can see how to manually install. Or you can search for same howto install new kernel. I think you can find something for 4.7 or 4.8 kernel.

I know how to install them manually... That is the whole reason for this thread. I don't want to install them manually. I want to add a PPA and then get updates automatically instead of having it to do myself every single time.

> **grahammechanical said:**
> For you it would be nice because that  is what you want. But for millions of other people it would not be nice  because it would risk breaking the OS for many people.

I didn't know Ubuntu desktop has millions of users... :D Care to share the link to that magnificent statistic... :popcorn: ?

> **grahammechanical said:**
> You are the kind of person who should be using the development version of Ubuntu.

No, I'm not :rolleyes:. Just because I want the latest stable mainline kernel, doesn't mean I want all my software to be alpha/beta... #-o

---

### Post by banceu_sergiu_ione on 2016-08-22
> **nw9165-3201 said:**
> Just because I want the latest stable mainline kernel, doesn't mean I want all my software to be alpha/beta... #-o

But you already run the latest stable mainline kernel. Aren't you ?

---

### Post by ian-weisser on 2016-08-22
> **nw9165-3201 said:**
> I want to add a PPA and then get updates automatically instead of having it to do myself every single time.

[...]

Also, why is this even called a PPA, if it is not a proper PPA?

[...]

But I want the latest kernels. I get automatic upgrades for the graphic drivers via the Oibaf PPA for example. So, I also want automatic updates for the latest kernels.

You clearly understand what a PPA is. But you seem to misunderstand what a PPA is for, the Ubuntu Kernel Team's workflow, and how stable updates are handled by apt and Ubuntu.
PPAs are not intended for stable updates of software in the Ubuntu Repositories. Some developers misuse PPAs for that purpose, but the Ubuntu Kernel Team is not among them.

If you want to test new kernels and file bugs, use the Kernel Team PPA.
If you want the latest already-tested kernels, use the linux-generic metapackage appropriate for your release of Ubuntu.
If you want kernel upgrades to be automatic (not recommended for testing!), then simply enable the option in Unattended Upgrades.

---

### Post by jaygambrel on 2016-09-08
Hi,

I don't know of any way to do this automatically with a ppa, but I ran across a script that will install an updated mainline kernel for you.  The thread is [http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

The script is located at [https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

I have never used this, but it might be useful for you if you are able to find a way to automate it.

I hope this is somewhat helpful.

Jay

---

