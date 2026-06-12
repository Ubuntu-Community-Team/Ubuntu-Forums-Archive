---
title: "PPA for most recent kernel"
date: 2014-06-26
forum: General Help
---

### Post by Tristan_Williams on 2014-06-26
I am running Xubuntu 14.04, with kernel 3.13.0-29
I noticed that on the kernel archive site, the most recent stable release is 3.15.2

Is there a PPA which will provide the more recent kernel and provide updates accordingly, instead of me having to download and build from source?

---

### Post by Bashing-om on 2014-06-26
Tristan_Williams; Hey !

Yepper !

See;
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

[INDENT][INDENT]all in the care and feeding
[INDENT][INDENT][INDENT]of your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by papibe on 2014-06-26
Hi Tristan_Williams.

I had to install an upstream kernel to test a possible [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630").

You may try the same method. [Here]("https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds")'s how to do it.

Hope it helps. Let us know how it goes.
Regards.

P.S.: IMHO unless you are not suffering from a bug that cripples your system, or you are looking for a new functionality yet not available, I don't see any value on using an upstream kernel.

---

### Post by grahammechanical on 2014-06-26
Ubuntu 14.04 will get a point release upgrade in July. That will bring in later kernels to keep Ubuntu up to date with the progress made by the Linux developers in supporting newer hardware in Linux. In fact, 14.04 will get 5 point release upgrades by the time 16.04 is released.

---

### Post by monkeybrain20122 on 2014-06-26
Create a folder somewhere, say call it 'kernel' in Downloads. Go to Bashing-om's link and choose the kernel you want, download 3 packages to ~/Downloads/kernel: linux-headers-all, linux-headers amd64 or i386 depending on whether your OS is 64 or 32 bit, linux-image amd64 or i386. Then open a terminal
```
cd Downloads/kernel
sudo dpkg -i *.deb
```

That's it.

In case something goes wrong, reboot, press shift when boot to see the grub menu, choose "advanced options" and boot into an earlier kernel and remove the packages you just installed say, using, synaptic.

---

### Post by Tristan_Williams on 2014-06-26
Yes, that's the Kernel I am wanting, but I wanted to know if there is a PPA for it?
I want to avoid manually installing, unpacking, or typing commands.

So to clarify, what PPA can I put into the following command:
```

sudo add-apt-repository [KERNEL-PPA]

```

---

### Post by monkeybrain20122 on 2014-06-26
> **Tristan_Williams said:**
> 
So to clarify, what PPA can I put into the following command:
```

sudo add-apt-repository [KERNEL-PPA]

```

No, not that I know of. What is the problem of downloading the files and typing TWO commands? If you don't want to do that just wait for 14.0.4.1 like grahammechanical said.

---

### Post by Tristan_Williams on 2014-06-27
> **monkeybrain20122 said:**
> No, not that I know of. What is the problem of downloading the files and typing TWO commands? If you don't want to do that just wait for 14.0.4.1 like grahammechanical said.

The only problem is that I will forget that I manually installed it so I won't be getting any of the updates. The reason for having a PPA would be to automatically get the updated versions when all the other packages on the system get updated.

It's not that big of a deal to have the latest kernel, I just thought that SURELY someone would have made a PPA for the mainline kernel

---

### Post by monkeybrain20122 on 2014-06-27
Well if it is working for you why do you want it constantly updated?

---

