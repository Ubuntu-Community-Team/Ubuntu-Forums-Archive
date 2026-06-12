---
title: "Building kernel - Only support what's needed"
date: 2014-03-01
forum: General Help
---

### Post by Tristan_Williams on 2014-03-01
I am going to compile and install Kernel 3.13.5

I would like to only use the options relevant to my system.
For example, I have a Dell Desktop, so why would I need Macintosh support? Or Amateur Radio Support? Or support for IDE drives?

What is the best way to find out which options I do and do not need?

---

### Post by tgalati4 on 2014-03-01
Turning off support for various hardware will make the loaded kernel smaller, and may reduce boot time.  Will a smaller kernel run faster?  Yes, definitely, in fact I saw a comparison between Gentoo (which is always compiled just for your specific hardware) and Ubuntu and there was a whopping 2% increase in speed.  So now you have to ask yourself, is 2% worth the agony units of compiling your own kernel?  Only you can decide.

Normally you would compile a list of loaded modules (*lsmod*) used in your target system.  Then as you go through the kernel configurator, you turn off the hardware you don't intend to use.  Having the *lsmod* list will help in this process.  Because of the multi-layered architecture in linux, disabling some hardware support may break software frameworks.  That is a trial-and-error process.

For instance here is a partial list of my loaded modules:

lp                     17760  0 
**parport                46346  3 parport_pc,ppdev,lp**
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
ahci                   25721  2 
libahci                31273  1 ahci
ssb                    52275  2 b43,ssb_hcd
tg3                   148928  0 

Now, I know I don't have a parallel port on this laptop, so I could safely assume that I can remove parallel port support.  But then I see it depends on lp, which I believe is a line printer module.  So if I delete parport support, it may break printing.  A second example.  I have a firewire port on this laptop.  But let's say I don't ever plan to use it, can I safely remove firewire support?  Perhaps, but it may break something else related to I/O.  It's best to take small steps at turning off things, but then that means a lot of kernel compiles--at 2 to 3 hours apiece.

Be sure to preface any future support requests on this forum with:  "I have a custom-compiled kernel and I am having trouble with . . ."

---

### Post by ibjsb4 on 2014-03-02
As tgalati4 said:

```
lsmod
```

Will list all loaded modules.  You can also get some clues as to what a module is doing with the modinfo command.  Example:

```
modinfo -v parport

```
You can also experiment with removing modules.  Example:

```
sudo modprobe -r parport

```
This is for one session only, a reboot will restore the module.

Its a good learning experience, but tgalati4 I think is right.  Little to be gained.

---

### Post by buzzingrobot on 2014-03-02
I built quite a few kernels years ago.  Today, I don't see a need.  Modules in a kernel that are not needed are not loaded.  So, if the unneeded bits are not compiled into a kernel, then what you get is a marginally smaller kernel image on the disk.

---

