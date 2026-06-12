---
title: "AMD Radeon 580 Causes Kernel Panic"
date: 2018-09-09
forum: General Help
---

### Post by megaboz2 on 2018-09-09
Full disclosure: I'm a Linux noob.  

Anyway, I recently installed a Radeon 580 in my tower, and I appear to be getting kernel panics after selecting Ubuntu from the grub menu on startup.  Here's my specs:

Ubuntu 18.04.1, 4.18.7 kernel (dual-booting with Windows 10 Pro)
Mesa 18.0.5
AMD Ryzen 2400G
G.Skill 16GB DDR4 2933Mhz
Asus ROG B350-F motherboard
AOC Freesync G2460VQ6 monitor
Sapphire Nitro+ Radeon RX 580 8GB

I'm just using the default Mesa drivers currently, although the same thing happened with the amdgpu drivers (now uninstalled).  The 2400G by itself (prior to installing the 580, and also if I now plug the monitor into the onboard DP instead of the 580) boots into Ubuntu just fine.  The 580 is confirmed as working flawlessly in Windows, so this doesn't appear to be a hardware failure.  Kernel panics occurred with kernel version 4.15.0.33.36 as well.

Any chance of getting this thing to boot up using the 580, then?


Thanks,
MB

---

### Post by Yellow Pasque on 2018-09-09
> **megaboz2 said:**
> I'm just using the default Mesa drivers currently, although the same thing happened with the amdgpu drivers (now uninstalled).

That doesn't make any sense. Mesa/Gallium3D is the 3D acceleration part of the driver. Even while you are using the "radeonsi" Mesa driver, you are still using the "amdgpu" kernel module.
Were you referring to amdgpu-pro?

---

### Post by megamini on 2018-09-10
Hello, I've reported a [similar issue]("https://ubuntuforums.org/showthread.php?t=2400576&highlight=rx+580") 2 days ago, and I'm still looking for a solution :-/

---

### Post by megaboz2 on 2018-09-10
> **Temüjin said:**
> That doesn't make any sense. Mesa/Gallium3D is the 3D acceleration part of the driver. Even while you are using the "radeonsi" Mesa driver, you are still using the "amdgpu" kernel module.
Were you referring to amdgpu-pro?

Note the first sentence of my original post :) .  My understanding was that Mesa drivers come pre-installed with 18.04.1, and that AMD offers their own drivers based on the open-source ones via their support site.  I have tried using the 580 both with and without the drivers from AMD's site installed, and in both cases I get a kernel panic upon startup.  Currently, all that is installed are the pre-installed Mesa drivers; if that includes amdgpu, I stand corrected.  The AMD drivers provide the option for either amdgpu or amdgpu-pro to be installed, giving the impression to someone who doesn't know any better *points at self* that amdgpu drivers were not pre-installed with the OS.

With that out of the way, anyone have suggestions on how to fix this?


Thanks,
MB

---

### Post by megaboz2 on 2018-09-10
> **megamini said:**
> Hello, I've reported a [similar issue]("https://ubuntuforums.org/showthread.php?t=2400576&highlight=rx+580") 2 days ago, and I'm still looking for a solution :-/

I wish I could offer advice, but yeah, we seem to be in the same boat.  If anyone responds here with a working solution, I'll make sure to reply to your thread with a link to mine :) .


Good luck,
MB

---

### Post by QIII on 2018-09-10
Just as a check, would you please post the results of 

```
lsmod | grep amdgpu
```

to see if the amdgpu driver module is loaded?

What GPU was present when you installed Ubuntu?

---

### Post by megaboz2 on 2018-09-10
> **QIII said:**
> Just as a check, would you please post the results of 

```
lsmod | grep amdgpu
```

to see if the amdgpu driver module is loaded?

Sure thing, this is the result:

```

amdgpu               2940928  24
chash                  16384  1 amdgpu
gpu_sched              24576  1 amdgpu
ttm                   106496  1 amdgpu
drm_kms_helper        172032  1 amdgpu
drm                   458752  19 gpu_sched,drm_kms_helper,amdgpu,ttm
i2c_algo_bit           16384  2 igb,amdgpu

```

So, I guess that means "yes"?

> **QIII said:**
> What GPU was present when you installed Ubuntu?

I originally installed 18.04 months ago with just the Ryzen 2400G APU for graphics, and everything ran fine.  I installed the 580 recently and got kernel panics, tried reinstalling using 18.04.1 for the heck of it, and still received the same error.


--MB

---

### Post by megamini on 2018-09-12
> **megaboz2 said:**
> I wish I could offer advice, but yeah, we seem to be in the same boat.  If anyone responds here with a working solution, I'll make sure to reply to your thread with a link to mine :) .

Anyway I'm following your thread, it got a bit more popular than mine. I also reported my issue on amd community forum, but no answer so far. Also I did not find much testimonies (positive or not) on the web about RX 580 with 18.04.
This guy seems to have it working:
[https://askubuntu.com/questions/1047182/dual-monitors-on-18-04-with-radeon-rx-580-gpu](https://askubuntu.com/questions/1047182/dual-monitors-on-18-04-with-radeon-rx-580-gpu)
He did not had the same issue, but maybe try this solution: "adding [FONT=trebuchet ms]amdgpu.dc=0[/FONT] to the kernel command line at boot". I switched back to my older card to get some work done, I'll do more testing this W.-E. if I get some time.

---

### Post by megaboz2 on 2018-09-12
> **megamini said:**
> maybe try this solution: "adding [FONT=trebuchet ms]amdgpu.dc=0[/FONT] to the kernel command line at boot".

Thanks for the heads-up on that, Mega.  I'll give it a try -- right after I find out how to edit the kernel command line ;-).  If I get that working, I'll let you know how it went.


--MB

---

### Post by megaboz2 on 2018-09-12
Huh, potentially interesting discovery.

So, I did a little searching to find out more about the "amdgpu.dc=0" setting before committing to changing the boot parameters (as described here: [https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter)), and I ran across this extremely long discussion regarding a Linux display bug encountered with AMD drivers: [https://bugs.freedesktop.org/show_bug.cgi?id=91880](https://bugs.freedesktop.org/show_bug.cgi?id=91880).  Skipping to the bottom of the replies, there's a list of boot settings relating to amdgpu that other users see when they edit the grub.cfg file to change amdgpu.dc to "0", namely something like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="radeon.cik_support=0 amdgpu.cik_support=1 amdgpu.modeset=1 amdgpu.dc=1 amdgpu.dpm=1"
```

However, my grub.cfg file just has this line instead:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Now, I know I have the Mesa drivers installed, since they come with the OS and they're listed in Synaptic when I do a search.  Doing a search in Synaptic for amdgpu, though, I only see the following installed:

libdrm-amdgpu1
libdrm-amdgpu1:i386
xserver-xorg-video-amdgpu

The following files are also listed in the search result as available, but are not installed:

xserver-xorg-video-amdgpu-dbg
xserver-xorg-video-amdgpu-hwe-16.04
xserver-xorg-video-amdgpu-hwe-16.04-dbg

Given all this, does it look like I have a full install of the Mesa/amdgpu drivers for the 580?   Pasting the first code block into grub.cfg to overwrite "quiet splash" just resulted in more kernel panic vomit text on startup, so either I actually do not have drivers installed correctly, or the amdgpu=0 solution simply doesn't work in my case, either.  Needless to say, I could use some additional insight from others out there.


--MB

---

### Post by megaboz2 on 2018-09-14
It seems I managed to find a solution to my little kernel panic problem after all.  A bit of background for context...

After doing a fresh install of Ubuntu on my hardware, I was getting a blip of error text prior to the login screen appearing.  Most of it referred to an "ACPI exception" error (which I still need to research, but is probably unrelated to this thread), but the second to last line stated: ```
AMD-VI: Unable to write to IOMMU perf counter.
```  I was just ignoring this error text because as long as I wasn't plugged into the 580, everything booted ok.  

Now, doing a bit of searching on AMD's support forum for open-source AMD topics, someone mentioned (and I lost the URL, sorry) that there have been issues with memory management in Linux with AMD GPUs, and that by turning off the IOMMU on startup, that solved the problem for them (they were getting black screens instead of kernel panic text).  So, I changed my grub config like so:

```
GRUB_CMDLINE_LINUX_DEFAULT="open splash iommu=soft"
```

...and voila!  I was able to boot to the desktop on my 580 :o!


--MB

---

