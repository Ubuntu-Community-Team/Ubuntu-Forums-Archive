---
title: "Dual Core and gutsy"
date: 2007-10-18
forum: General Help
---

### Post by chrishere01 on 2007-10-18
so yeah my dual core processor is only using one core
i need help geting the other to work
plze
thanx

---

### Post by dabl on 2007-10-18
I'm not sure how you do that (get it to run only one core).

You should be using the "AMD_64" Ubuntu Gutsy version.  When you open a console and input```
 cat /proc/cpuinfo
``` you should get something similar to the following:


> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         X6800  @ 2.93GHz
stepping        : 6
cpu MHz         : 3329.994
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6664.35
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         X6800  @ 2.93GHz
stepping        : 6
cpu MHz         : 3329.994
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6660.11
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

:)

---

### Post by steveneddy on 2007-10-18
What is the output of

```
uname -a
```

---

### Post by chrishere01 on 2007-10-18
no i only have one 
enabled
how can you get another one enabled

---

### Post by chrishere01 on 2007-10-18
damn i dont think im using the amd version
any way to change this
a quick fix perhaps

---

### Post by chrishere01 on 2007-10-18
Linux home-desktop 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux

---

### Post by Athanasius on 2007-10-18
Maybe you can choose in the BIOS at startup?

---

### Post by chrishere01 on 2007-10-18
> **Athanasius said:**
> Maybe you can choose in the BIOS at startup?

hmmm not sure about that

---

### Post by chrishere01 on 2007-10-18
SOOOOOOOOOOOoooo yeah still need help

---

### Post by steveneddy on 2007-10-18
> **chrishere01 said:**
> Linux home-desktop 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux

You are running a 32 bit Ubuntu OS without SMP kernel installed.

I believe you want to run the generic kernel and not the i386 kernel.

This will give you support for both cores.

Why don't you run 64 bit instead? That is actually 64 bit architecture, isn't it?

---

### Post by steveneddy on 2007-10-18
> **chrishere01 said:**
> SOOOOOOOOOOOoooo yeah still need help

Yeah...welllllll...give everyone a chance to help everyone else here, fella. These are free and volunteer, so have patience please.

---

### Post by steveneddy on 2007-10-18
And stop [dual posting]("http://ubuntuforums.org/showthread.php?p=3564576#post3564576")!

---

### Post by chrishere01 on 2007-10-18
hmm im not sure

is there anyway i could command this so i can get to 64 bit or amd structure or any thing


i see what you guys are telling me 
how do i fix this

---

### Post by chrishere01 on 2007-10-18
> **steveneddy said:**
> And stop [dual posting]("http://ubuntuforums.org/showthread.php?p=3564576#post3564576")!

lol here is fine
srry bout this ive been asking for about 3 days so yea i just gave up
and kinda advertised :D

---

### Post by steveneddy on 2007-10-18
> **chrishere01 said:**
> hmm im not sure

is there anyway i could command this so i can get to 64 bit or amd structure or any thing


i see what you guys are telling me 
how do i fix this

You would have to do a total reinstall to go 64 bit.

I forgot how to do it in the terminal, but you can open Synaptic and choose all of the linux-generic listings for the kernel, install them and reboot, choose the generic kernel and go man, go!

Linux-generic

linux-headers

linux-image-generic

Don't forget to restart.

You may want to do a search on upgrading the kernel. It's out there but I can't find it.

---

### Post by chrishere01 on 2007-10-18
oh hmm 
im not sure if its 64 bit  though
i hope it will intall to the right thing

---

### Post by steveneddy on 2007-10-18
> **chrishere01 said:**
> 
im not sure if its 64 bit  though


it's not - the kernel info you posted was a 32 bit kernel. It's the i386 kernel.

---

### Post by chrishere01 on 2007-10-18
im not sue if my processer is 64 bit tho?
but ill try to update anyways
and steven it didnt work ;(

---

### Post by sci-fi guy on 2007-10-18
If you have a 32-bit processor, the 64-bit LiveCD will tell you so and not boot.

---

### Post by chrishere01 on 2007-10-18
hmmm i see sci-fi guy
ill just stick with 32 bit fornow
but how can i get my other processor working
cause its not

---

### Post by steveneddy on 2007-10-18
You must install the correct linux kernel to get both processors working.

---

### Post by chrishere01 on 2007-10-18
hmm
soo hmm
damn hmm
lemme try the the fiesty fawn 64 bit one

---

### Post by jespdj on 2007-10-19
Why do you think that only one core is used? What did you see that convince you that only one of the cores is used?

You do not need the 64-bit version to get both cores working. If you have a dual-core processor, then Ubuntu will use both cores automatically.

---

### Post by steveneddy on 2007-10-19
Here is the output to his uname -a

```

Linux home-desktop 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux

```

looks like the kernel without SMP support to me.

---

### Post by dabl on 2007-10-20
I'm guessing it's not actually a dual core CPU, (or else the mobo doesn't support dual cores), because SMP isn't even a kernel choice anymore -- it is automatically installed if a dual-core processor is detected.  Intel's CPU naming schemes are less than crystal clear (deliberately, I'm sure).  They've got Pentium Dual Core, Core 2 Duo, Pentium D, Pentium 4, Pentium Extreme Editions, blah blah blah and you'll have to read the fine print in the specs to figure out which ones are actually dual cores.  You can start here, but you'll quickly get lost in the rabbit trails that go to the CPU lines:

[http://www.intel.com/technology/computing/dual-core/index.htm?iid=prod_desk+1_dc](http://www.intel.com/technology/computing/dual-core/index.htm?iid=prod_desk+1_dc)

:lolflag:

---

### Post by rand0m on 2007-10-21
Okay so I'm having a similar problem with Kubuntu 7.10. This is a clean install but I know for a fact that I have a dual core cpu (e4300, not a noob to hardware). It worked fine in Feisty and Windows. I just noticed that only 1 cpu shows up when I installed conky and it said: "Conky: attempting to use more CPUs then you have!" I'm using the same exact hardware. What's the deal?

[COLOR="Red"]uname -a[/COLOR]:
```
Linux mickey 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux

```

[COLOR="Red"]/proc/cpuinfo[/COLOR]:
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping        : 2
cpu MHz         : 1668.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5007.60
clflush size    : 64

```

---

### Post by rand0m on 2007-10-21
Bleh, figured it out. My grub menu boots off 1st option w/ an escape option to go to the menu instead of displaying menu w/ an escape option like before. So I actually went to the menu this time and noticed the default was the i386 kernel instead of the generic which is lower on the menu. Edited the menu and now all is well. Dual cores back in action :)

---

### Post by tschoel on 2007-10-23
I second the last post.  Had the same problem with an upgrade to Gutsy, and found the same fast resolution by changing this.  Thanks for the help.

---

### Post by rand0m on 2007-10-24
BTW, the option that skipped the grub menu was called "hiddenmenu" in /boot/grub/menu.lst

---

### Post by supercoco on 2007-10-29
> **chrishere01 said:**
> so yeah my dual core processor is only using one core
i need help geting the other to work
plze
thanx

I had the same problem after upgradiny from edgy and fixed it reinstalling the package lm-sensors
with synaptic

---

