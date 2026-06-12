---
title: "Making kernel compiles from kernel.org similar to edgy kernel"
date: 2007-03-15
forum: General Help
---

### Post by quark_77 on 2007-03-15
Hi All,

I have been following the Master Kernel Thread on this forum for a HOWTO on how to build the kernels available from kernel.org. I have run into a number of issues, which I'd like to ask about.

My hardware specs are as follows: Intel Core 2 Duo, ATI Mobility Radeon, SCSI Hard disks (the ones found in IBM Thinkpads, as that is what I have) + other bits.

I have successfully built and run the kernel 2.6.7.20.2, but as you can imagine have run into problems relating to those restricted-modules packages:
[LIST]
[*]3d acceleration does not work. I need fglrx to do this, so I downloaded the appropriate driver from ati.amd.com, ran the installer and now have fglrx source installed to /usr/src/modules/fglrx. My question here is - if I run a compile of /usr/src/linux will it build the modules it needs from /usr/src/modules? i.e. will it build and use fglrx too?
[*]I cannot get ipw3945, needed for my wireless adapter, to build at all, under the latest stable edgy kernel or my custom one. Neither can I build IEEE802.11 or patch my kernel sources with it, despite the fact I think the kernel sources are the most recent anyway. What do I do with respect to these drivers / how do I get ipw3945 to build?
[*]I have a dual core system. Running uname -r gives me all the expected output except for SMP which gives #1. Is this custom kernel picking up my two processors? If not, how do I get it to do that?
[*]The new kernel picks up my primary and only hard drive as sdb - I can only presume sda has been reserved for the CD-ROM drive or some other device - how can I ensure my hard disk is picked up as sda? I'd rather not modify fstab when changing between kernels! Or menu.lst!
[*]Finally, the Ubuntu documentation suggests the Ubuntu developers make a number of changes and apply patches to the kernel. How do I find out what patches they apply and which ones I might need?
[/LIST]

I am aware the Ubuntu docs tell us not to play if we don't know what we are doing but I'd rather learn this way and understand more about Linux than just use it, plus I'd have a more up to date kernel this way..!

Thanks in advance for your help, please post anything you think might help even if it only applies to half of one of the above points!

Quark_77

---

### Post by mbeierl on 2007-03-15
The dual core stuff is in the kernel config, under

Processor Type and Features ->  
Symmetric multi-processing support (SMP)
Processor Family -> Core 2/newer Xeon (MCORE2)
Mutl-core scheduler support (SCHED_MC)

As for ATI stuff, sorry, I have an Intel graphics card, can't help.  The patches from the Ubuntu team may be backports of security or critical bugs from later kernels to the currently shipped kernel.  If you're building the latest kernel, there are no patches.

Well, not true: there are user add on patches, such as fbsplash and vesa-tng (to give a nice hi-res console) and suspend2 (to make a reliable, customizable, and pretty hibernate/resume), and well as some performance "hacks" (Con Kolivas patchsets).

When building a new kernel, you should always start with a make oldconfig to bring your current kernel settings forward, then make xconfig (or menuconfig) to customize it from there.

---

### Post by quark_77 on 2007-03-15
Hi mbeierl,

Ok, thanks for your help. I presume the Ubuntu folks apply the rc patches for various security fixes then - that makes sense.

I had previously set the processor to 586 as I presumed this was what the generic kernel was set to, I shall experiment the Core 2 option and see if that produces any better results.

I have a HOWTO regarding fglrx (ATI's driver) sources, so when I next build the kernel I shall try this as well to see if it works.

Regarding the SCSI problem, how would I work out what the kernel thinks sda is? As it seems to prefer sdb for my hard disk despite the fact I have no other hard disks installed! I shall try the oldconfig method first and will post back the results in a few days time!

Thanks again,

Quark_77

---

### Post by mbeierl on 2007-03-16
Just a thought:

I noticed in /etc/modprobe.d/blacklist-pata:

```

# There are two possible drivers for each PATA (old IDE) controller,
# the newer libata driver that exposes the drives as /dev/sd* and the old
# ide subsystem driver that exposes the drives as /dev/hd*.
#
# Choose wisely, my friend.

```

I'm wondering if your cdrom was ide and it's now being picked up with the new kernel as pata, which makes it sdx, instead of hdx...

---

### Post by quark_77 on 2007-03-18
Hi mbeierl,

I have copied the ubuntu config from /boot/config-'uname -r' and used make oldconfig, adjusted the setup with SMPs as you suggested. This fixes the sda problem for the hard disk, I think because libata is not enabled, as you have suggested. The SMP problem refuses to be fixed, even with SMP enabled, scheduling enabled and Core2/Xeon... I shall keep fiddling with the options - perhaps I have enabled something that shouldn't be.

I have done some research on the ubuntu kernel itself, too. The ubuntu kernel is "hardened" with [the grsecurity patch]("http://www.grsecurity.com") and [suspend]("http://www.suspend2.net") amongst others. Other changes are also made, although these I think are simply build optimisations. I have built & applied grsecurity without issue to 2.6.19.3, the latest available kernel.

ATI require we run their installer and create fglrx-kernel-sources.deb, install these, copy /usr/src/modules/fglrx to /usr/src/linux/modules/fglrx. It should then build under the modules_image command, although at present, it doesn't.

The same goes for ipw3945, which is located at /usr/src/linux/drivers/net/wireless/ipw3945. The microcode must be installed, and the binary daemon, then finally the kernel built to produce the module.

Sadly, I can't get the thing to build, although no doubt I will succeed in the end!

Thanks for your help!

Quark_77

---

### Post by scxtt on 2007-03-18
here's the steps i use to get fglrx working for my x850pro:
[indent]-- download ati-driver-installer*.run from website

-- sudo apt-get install module-assistant build-essential 
-- sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

-- chmod +x ati-driver-installer*.run
-- ./ati-driver-installer*.run --buildpkg Ubuntu/<release name, i.e. Dapper, Edgy>

-- sudo dpkg -i xorg-driver-fglrx*.deb 
-- sudo dpkg -i fglrx-kernel-source*.deb
-- sudo dpkg -i fglrx-control*.deb

-- sudo rm /usr/src/fglrx-kernel*.deb

-- sudo module-assistant prepare,update
-- sudo module-assistant build,install fglrx
-- sudo depmod

-- sudo aticonfig --initial
-- sudo aticonfig --overlay-type=Xv[/indent]
pretty common way of doing it, but it's worked for me w/ version 8.26.18 and 8.34.8 on Dapper and Edgy (and even in DreamLinux, another .deb-based distro) ...

---

### Post by mbeierl on 2007-03-19
The stock Ubuntu kernel uses the kernel suspend, not suspend2.  There is a difference - I know as I cannot use the stock kernel suspend.  I must apply the suspend2 patch to all my kernels.  But that is very odd about the smp stuff...

Oh - wait.  What is that #1 for anyway.  Try cat /proc/cpuinfo.  Here's mine:

```

uname -a
Linux ottws58 2.6.21-rc3 #1 SMP Mon Mar 12 21:40:21 EDT 2007 i686 GNU/Linux
mark@ottws58:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3997.45
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3994.10
clflush size    : 64

```

---

### Post by quark_77 on 2007-04-03
Hi Everyone,

Thanks for your help. I set MCORE2=y and X86_GENERICARCH=y amongst others and used make oldconfig using the edgy config file - this imported the relevant settings to make my SATA/SCSI HDs show up as sda as opposed to sdb...

ipw3945 & fglrx don't compile with 2.6.20.4 without a little persuasion... well, a patch for fglrx fixes the problem and then either make-kpkg modules_image or sudo m-a build,install works.

As for ipw3945, I found a patch for the kernel that installs this driver. Placing the microcode in /lib/firmware/(uname-r)/ipw3945.ucode and the daemon as /sbin/ipw3945d-(uname -r) works although you need to run uname -r under your custom kernel.

Thanks for your help, I've learnt an awful lot. My post on the master kernel thread [http://www.ubuntuforums.org/showpost.php?p=2394938&postcount=232](http://www.ubuntuforums.org/showpost.php?p=2394938&postcount=232) links to the patches I used and where I found them.

In terms of what the ubuntu team do to the kernel - grsecurity & PaX are two patches considered ... amongst other changes. I don't really know, all I've found out is grsecurity breaks fglrx & ipw3945 builds amongst others.

Thanks again

Quark_77

---

