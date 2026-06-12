---
title: "HP Elitebook 840 G5 - Feels slower compared to others"
date: 2019-07-14
forum: General Help
---

### Post by l4a-hf0 on 2019-07-14
Hi all

Firstly, I apologise sincerely if this topic has already been discussed on this forum.  I've done some searching and nothing came up, hence the post.

I'm new to the forum.  This is my first post.  I'm new to Ubuntu, but not to Linux.  But, that said, I haven't really dabbled in Linux on a full-time basis since leaving University about 15 years ago.  

Here's my dilemma:  I've installed Ubuntu 18.04LTS (off the same Ubuntu Live USB) on the following three laptops:


[LIST=1]
[*]Microsoft Surface Pro 4 - i5 processor (4 cores); 4GB RAM; 256 GB SSD (dual boot with Win10)
[*]Apple MacBook Pro - i7 processor (8 cores); 16GB RAM; 512 GB SSD (dual boot with MacOS)
[*]HP Elitebook 840 G5 - i5 processor (8 cores); 16GB RAM; 512 GB SSD (single boot)
[/LIST]

On the first two systems, firstly, the installation process completed quicker than on the third system even though all the same options were used.

On the first two systems, Ubuntu feels snappy, fast, a pleasure to use.  The System Monitor shows a nice even graph for each core and no core ever uses more than 20% CPU.  The consumption on the MBP, in fact, is super low, with no one core ever going above 5%.  Memory consumption on the three is as follows:  Surface = 50%, MBP = 12%, Elitebook = 12%.

The third system, the Elitebook, is the newest of the three.  The Surface is about 2 years old.  The MBP about 4 years old.  The Elitebook is under a year old.

**The Elitebook is very sluggish. ** The System Monitor shows a much higher CPU consumption.  One of the eight cores will always be close to 40% (each core will take turns going high, one core will be high and the rest 7 will be low).  The graph also isn't smooth, and looks quite bumpy compared to the other two.

When clicking on the 9-dots icon for Applications, on the Elitebook, it takes a second or two for the icons to appear.  The same action is instantaneous on the other two laptops, including on the Surface which you can see really has quite shameful specs compared to the rest.  When I click on the 9-dots again (on the Elitebook) to exit the Applications screen, a "ghosting" effect can be seen where the icons don't disappear instantly but takes a second or so to completely go away.  The MBP and Surface are instantaneous in this regard as well.

Despite all three installs having taken place from the same USB stick, the MBP and Surface have ended up with different software versions of certain system tools.  As an example, take the aforementioned System Monitor tool:  The Elitebook's version is 3.28.2.  The MBP and Surface have ended up with 3.31.something.

All three installs were done with Wifi enabled and connected to the internet.

Functionally, the Elitebook install seems complete (as well as the other two).  All hardware works on all three installations.  The only difference is this performance lag that is getting quite annoying to deal with on the Elitebook.

I've reinstalled Ubuntu a few times on the Elitebook, with different options enabled, and the end result is the same.  I've also turned Swappiness down to 10 (on the Elitebook only) to minimise swap and that's make a minuscule difference, possibly even just a placebo.

All three systems are SSD based.  The Elitebook and MBP are spec'd to deal with heavy lifting whereas the Surface is just a web surfing machine.  It saddens me therefore, and confuses me to no end, that the Surface outperforms the Elitebook.

Some guidance is sought on this matter.

Regards.

PS!  Forgot to mention, on the Elitebook, the CPU graphs tend to settle down somewhat, and consumption drops a bit, when I turn networking off (i.e. Wifi off or Wired connection off).  Still, the graphics performance is quite poor on the Elitebook regardless and overall the laptop feels less snappy than the Surface and MBP.

---

### Post by cruzer001 on 2019-07-15
Hello and welcome to the forums :)

That HP should be just as fast as your others.  Maybe you just need a proper video driver.  Whats the video specs on that HP?
```
lshw -c video
```
And what is the "model name" of that processor?
```
lscpu
```

---

### Post by l4a-hf0 on 2019-07-15
> **cruzer001 said:**
> Hello and welcome to the forums :)

Thanks cruzer001

> **cruzer001 said:**
> That HP should be just as fast as your others.  Maybe you just need a proper video driver.  Whats the video specs on that HP?
```
lshw -c video
```
And what is the "model name" of that processor?
```
lscpu
```

Some outputs:

```

_uname -a_

Linux xxxxxxxx-HP-EliteBook-840-G5 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

_lshw -c video_

  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: iomemory:1f0-1ef iomemory:1f0-1ef irq:132 memory:1ff2000000-1ff2ffffff memory:1fc0000000-1fcfffffff ioport:3000(size=64) memory:c0000-dffff

_lscpu_

Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              8
On-line CPU(s) list: 0-7
Thread(s) per core:  2
Core(s) per socket:  4
Socket(s):           1
NUMA node(s):        1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               142
Model name:          Intel(R) Core(TM) i5-8350U CPU @ 1.70GHz
Stepping:            10
CPU MHz:             400.004
CPU max MHz:         3600.0000
CPU min MHz:         400.0000
BogoMIPS:            3792.00
Virtualisation:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            6144K
NUMA node0 CPU(s):   0-7
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp

```

---

### Post by cruzer001 on 2019-07-15
Your running Intel UHD Graphics 620 and there seems to be more than one choice for you.  Using the GUI will make it easy to try driver options.

In your applications locate **Software & Updates** then go to the **Additional Drivers** tab.  There you will see your driver options.  Try them.  This would  be my first choice.
  
There is a lot of talk out there about the 620 and linux.  Some claim a kernel upgrade will fix this.  Others say upgrading to 19.04 is the fix.  Others have extremely long command line fixes.  Makes it tough on figuring out the best route to go.

Another possibility
[https://forums.linuxmint.com/viewtopic.php?t=261389](https://forums.linuxmint.com/viewtopic.php?t=261389)

Don't forget to cross fingers and hold tongue just right :)

---

### Post by cruzer001 on 2019-07-15
> Linux xxxxxxxx-HP-EliteBook-840-G5 4.15.0-29-generic
I overlooked this!  Your not up to date, could be as simple as that.
```
sudo apt update && sudo apt upgrade -y
```
Now check out your machine and kernel.
```
uname -r
```

---

### Post by l4a-hf0 on 2019-07-15
> **cruzer001 said:**
> I overlooked this!  Your not up to date, could be as simple as that.
```
sudo apt update && sudo apt upgrade -y
```
Now check out your machine and kernel.
```
uname -r
```

cruzer001, I owe you my sincerest gratitude.  I first tried some of the suggestions on the Linux Mint forum link that you posted, specifically these steps:


[COLOR=#333333][FONT=&amp]1. sudo apt install xserver-xorg-hwe-16.04 xserver-xorg-input-all-hwe-16.04[/FONT][/COLOR]
[FONT=Lucida Grande][COLOR=#333333]2. sudo nano /etc/default/grub and then edit the line [/COLOR][/FONT][COLOR=#333333][FONT=&amp]GRUB_CMDLINE_LINUX_DEFAULT="[/FONT][/COLOR][COLOR=#333333][FONT=&amp]quiet[/FONT][/COLOR][COLOR=#333333][FONT=&amp] splash" to add "[/FONT][/COLOR][COLOR=#333333][FONT=&amp]i915.alpha_support=1[/FONT][/COLOR][COLOR=#333333][FONT=&amp]"[/FONT][/COLOR]
[FONT=Lucida Grande][COLOR=#333333]3. sudo update-grub[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#333333]4. reboot[/COLOR][/FONT]

[FONT=Lucida Grande][COLOR=#333333]This actually made a noticeable difference, but some of the lag was still here.  

However, what you posted above about not being on the right version _**did the trick.**_

After running apt update/upgrade, I'm now on...

[/COLOR][/FONT]```
_uname -r_

4.18.0-25-generic

```

...and the UI feels lag-free and almost as snappy as on the other two laptops.  

You are a legend.  Thanks immensely for your help.

---

### Post by l4a-hf0 on 2019-07-15
```
[COLOR=#333333]1. sudo apt install xserver-xorg-hwe-16.04 xserver-xorg-input-all-hwe-16.04
```[/COLOR]

Just a point, I opted to install [COLOR=#333333]xserver-xorg-hwe-18.04 xserver-xorg-input-all-hwe-18.04[/COLOR] in place of 16.04

---

### Post by cruzer001 on 2019-07-15
Right on, let the free beer flow
[https://media1.tenor.com/images/f39f11f4b068537aef41725adaa4ac32/tenor.gif?itemid=5996766](https://media1.tenor.com/images/f39f11f4b068537aef41725adaa4ac32/tenor.gif?itemid=5996766)

Till next we meet ):P

Don't forget
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by l4a-hf0 on 2019-07-16
Thanks again cruzer001.  I'm sure we'll "meet" again sooner than later, once I find myself stuck with the next Ubuntu task.

---

