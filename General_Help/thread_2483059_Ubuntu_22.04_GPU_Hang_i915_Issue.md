---
title: "Ubuntu 22.04 GPU Hang i915 Issue"
date: 2023-01-19
forum: General Help
---

### Post by bradwiggo on 2023-01-19
My computer (specs at bottom of post) keeps freezing, and sometimes completely locking up needing a hard reset. I have found the error in the syslog, I'll post it below. The issue seems to occur semi randomly, I can't tell what is causing it. So far it's happened 6 times: 

1. When editing code in Gedit and using the terminal
2. Same as above (had to hard reset)
3. Same as above 
4. In a VirtualBox VM
5. When editing code
6. When editing code and also using a web browser (had to hard reset)

Here is the error: (seems to be same every time so just posting on, I can post them all if needed to a pastebin)

> Jan 18 11:03:15 usernamelaptop kernel: [180359.703364] Asynchronous wait on fence 0000:00:02.0:gnome-shell[1820]:2f8d4 timed out (hint:intel_atomic_commit_ready [i915])
Jan 18 11:03:19 usernamelaptop kernel: [180363.551062] i915 0000:00:02.0: [drm] GPU HANG: ecode 12:0:00000000
Jan 18 11:03:19 usernamelaptop kernel: [180363.551118] i915 0000:00:02.0: [drm] Resetting chip for stopped heartbeat on rcs0
Jan 18 11:03:19 usernamelaptop kernel: [180363.555862] i915 0000:00:02.0: [drm] GuC firmware i915/adlp_guc_62.0.3.bin version 62.0 submission:enabled
Jan 18 11:03:19 usernamelaptop kernel: [180363.555871] i915 0000:00:02.0: [drm] GuC SLPC: enabled
Jan 18 11:03:19 usernamelaptop kernel: [180363.555874] i915 0000:00:02.0: [drm] HuC firmware i915/tgl_huc_7.9.3.bin version 7.9 authenticated:yes
Jan 18 11:03:19 usernamelaptop gsd-media-keys[2371]: [GFX1-]: GFX: RenderThread detected a device reset in PostUpdate

Specs: 

Lenovo Yoga Slim 7 Pro 14IAP7
i7-1260P with Integrated Iris Graphics (Mesa Intel® Graphics (ADL GT2))
16GB DDR5
512 NVME SSD
Ubuntu 22.04.1 LTS
Kernel: 5.15.0-58-generic 

Only been using the system with linux for about a month, haven't encountered this issue until a few days ago.

---

### Post by MAFoElffen on 2023-01-19
Edit with privileges in /etc/default/grub file, add the red boot parameter as a boot option:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash [COLOR=#ff0000]i915.enable_psr2_sel_fetch=0[/COLOR]"
GRUB_CMDLINE_LINUX=""

```
Then save, exit and 
```

sudo update-grub

```

---

### Post by bradwiggo on 2023-01-19
> **MAFoElffen said:**
> Edit with privileges in /etc/default/grub file, add the red boot parameter as a boot option:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash [COLOR=#ff0000]i915.enable_psr2_sel_fetch=0[/COLOR]"
GRUB_CMDLINE_LINUX=""

```
Then save, exit and 
```

sudo update-grub

```

Thank, I'll try this out and see if it works. It's super annoying to test as there is no reliable way to repeat the hang. 

What does this option do? Would it have an effect on performance? 

In my file, the line with the edit doesn't have the "--" in it. Does that matter?

---

### Post by MAFoElffen on 2023-01-20
I have added that double dash since around Ubuntu 12.04 LTS... It seems to let the kernel know that boot parameter options follow. Seems to help with some stubborn options to take, an not be ignored.

I looked up your error in bug reports from kernel.org, Red Hat, Debian, Intel, and other places. That parameter was the common fix noted. I'm not 100% on how to explain it, but this reddit thread explains it fairly well. Somehow ignores something that was causing a timeout waiting for a response that really shouldn't be there in the first place. I read some patches and code fixes, but, it is still happening. There was one more (different) that was in place of this, but it said that this specific option was more useful.
[https://www.reddit.com/r/linuxquestions/comments/yiiua7/does_anyone_know_what_the_status_is_on_the_i915/](https://www.reddit.com/r/linuxquestions/comments/yiiua7/does_anyone_know_what_the_status_is_on_the_i915/)

From [https://kernel.googlesource.com/pub/scm/linux/kernel/git/davem/sparc/+/refs/heads/master/drivers/gpu/drm/i915/i915_params.c](https://kernel.googlesource.com/pub/scm/linux/kernel/git/davem/sparc/+/refs/heads/master/drivers/gpu/drm/i915/i915_params.c)
```

i915_param_named_unsafe(enable_psr2_sel_fetch, bool, 0400,
    "Enable PSR2 selective fetch "
    "(0=disabled, 1=enabled) "
    "Default: 0");

```

[https://www.spinics.net/lists/intel-gfx/msg242777.html](https://www.spinics.net/lists/intel-gfx/msg242777.html)

---

### Post by bradwiggo on 2023-01-24
> **MAFoElffen said:**
> I have added that double dash since around Ubuntu 12.04 LTS... It seems to let the kernel know that boot parameter options follow. Seems to help with some stubborn options to take, an not be ignored.

I looked up your error in bug reports from kernel.org, Red Hat, Debian, Intel, and other places. That parameter was the common fix noted. I'm not 100% on how to explain it, but this reddit thread explains it fairly well. Somehow ignores something that was causing a timeout waiting for a response that really shouldn't be there in the first place. I read some patches and code fixes, but, it is still happening. There was one more (different) that was in place of this, but it said that this specific option was more useful.
[https://www.reddit.com/r/linuxquestions/comments/yiiua7/does_anyone_know_what_the_status_is_on_the_i915/](https://www.reddit.com/r/linuxquestions/comments/yiiua7/does_anyone_know_what_the_status_is_on_the_i915/)

From [https://kernel.googlesource.com/pub/scm/linux/kernel/git/davem/sparc/+/refs/heads/master/drivers/gpu/drm/i915/i915_params.c](https://kernel.googlesource.com/pub/scm/linux/kernel/git/davem/sparc/+/refs/heads/master/drivers/gpu/drm/i915/i915_params.c)
```

i915_param_named_unsafe(enable_psr2_sel_fetch, bool, 0400,
    "Enable PSR2 selective fetch "
    "(0=disabled, 1=enabled) "
    "Default: 0");

```

[https://www.spinics.net/lists/intel-gfx/msg242777.html](https://www.spinics.net/lists/intel-gfx/msg242777.html)

How would I add the second fix you (one in this quoted reply)

The first fix didn't work sadly, have had a couple of hangs in the last two days. 

Also how would I check that the original fix actually worked? (i.e. it actually disabled the feature) 

I found this and tried it, and it says it's still enabled: 

```
sudo cat /sys/kernel/debug/dri/0/i915_edp_psr_status
[sudo] password for ethan: 
Sink support: yes [0x03]
PSR mode: PSR1 enabled
Source PSR ctl: enabled [0x81f006e6]
Source PSR status: IDLE [0x04010000]
Busy frontbuffer bits: 0x00000000
```

however, that says PSR1

---

### Post by MAFoElffen on 2023-01-24
The additional quoted there is not a fix, but rather were, in the code, where that is applied and what it does...

File a bug with launchpad and they can get into more detailed tests and fixes. Please post the link to the Bug in a post here...

---

### Post by david3252 on 2023-02-25
I think I have similar issue

Do you already fix the problem ?
Thanks in advance

David

---

### Post by MAFoElffen on 2023-02-26
*Linux Kernel 5.15*... Do you have HWE Installed? On HWE "now", is 5.19.X. The i915 driver is in the Kernel. Wondering if the newer Kernel changes your situation(?)

That and Ubuntu LTS is now 22.04.2.

---

### Post by david3252 on 2023-02-26
Hello,
Thanks I just retry.
I'm on the 5.19.0-32-generic. I have just retry on an "old" 5.15 : 5.15.0-52, with the last 5.15.0-60 and with the last 6.1.0-1006oem. It is the same, it crash the same.
The 5.15 kernel have better 3D hardware support with VMWare. The DirectX diag with DirectX 7, 8, 9 work better. The cube is very fluid, it is not the case with the 5.19 or 6.1
Don't know if driver have been modify.

For all cases the log is very poor ... (dmesg, syslog, Xorg)
```

 kernel: [   30.424697] x86/split lock detection: #AC: main-svga/3123 took a split_lock trap at address: 0x5621f30a2e3d
kernel: [   30.611750] x86/split lock detection: #AC: vmx-svga/3120 took a split_lock trap at address: 0x55ea598febb7
kernel: [   30.628239] x86/split lock detection: #AC: main-mks/3122 took a split_lock trap at address: 0x5621f30a30a7

kernel: [    0.000000] x86/split lock detection: #AC: crashing the kernel on kernel split_locks and warning on user-space split_locks

```
Another time :
```

kernel: [   51.879397] split_lock_warn: 35 callbacks suppressed

```

It work very well until crash.

Thanks in advance
David

---

### Post by david3252 on 2023-02-26
If I put in sleep the computer, it work better after the sleep. If I hibernate the computer sometime its works like before the bug or minimally better than before hibernation.

A people deal with a lost of sync in an other topic or forum, it could be that. I think sleep or hibernate have only impact on the hardware.

The better effect I can measure is the interrupts :
Before the bug :
```

cat /proc/interrupts :  
150:          0      12500          0          0          0          0          0          0  IR-PCI-MSI 327680-edge      xhci_hcd
 130:          0          0         36          0          0          0          0          0  IR-PCI-MSI 212992-edge      xhci_hcd
 195:          0          0          0        765          0          0      43917          0  IR-PCI-MSI 32768-edge      i915

 NMI:          3          3          2          3          1          1          2          1   Non-maskable interrupts
 LOC:      44084      45148      38917      43380      44347      39950      63891      41043   Local timer interrupts
 SPU:          1          0          0          0          0          0          0          0   Spurious interrupts
 PMI:          3          3          2          3          1          1          2          1   Performance monitoring interrupts
 IWI:       1983       1796       1016       1318       1958       1772      34849       1872   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:       3202       2551       2333       2750       2945       2053       2450       1637   Rescheduling interrupts
 CAL:      32361      34041      33199      33443      32830      38261      30730      34866   Function call interrupts
 TLB:       4600       6819       7900       4979       5689       4671       7387       5792   TLB shootdowns
 **TRM:          2          2          2          2          2          2          2          2   Thermal event interrupts**

```

I stress and the bug start !
After the bug :
```

 195:       7550          0          0        765          0          0     964697          0  IR-PCI-MSI 32768-edge      i915
 150:       7011      37888          0          0          0          0          0      10041  IR-PCI-MSI 327680-edge      xhci_hcd
 130:         10          0         36          0          0          0          0          9  IR-PCI-MSI 212992-edge      xhci_hcd

 NMI:          4          6          6          4          1          1          4          3   Non-maskable interrupts
 LOC:     460124     453153     482067     473181     455918     460154     609368     463418   Local timer interrupts
 SPU:          1          0          0          0          0          0          0          0   Spurious interrupts
 PMI:          4          6          6          4          1          1          4          3   Performance monitoring interrupts
 IWI:      28098      23300      16538      19575      21421      22590     505527      24870   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:      23455      16173      11638      19702      12745      12816      11421      15952   Rescheduling interrupts
 CAL:     131999     114719     106123      98885     108117     112193     110945     100299   Function call interrupts
 TLB:      28703      24931      27732      24161      29120      27679      33927      25081   TLB shootdowns
 **TRM:      18027      18039      18034      18040      18039      18038      18027      18032   Thermal event interrupts**

```
What deal with Thermal event interrupts ?

Edit : it is the same with the Ubuntu 22.04 LTS Live USB Boot 

Thanks

---

### Post by MAFoElffen on 2023-02-26
There is a confirm problem with VMwares's vmx-svga module, especially when you try to enable 3D graphics in VM's. There are many threads on this in the VMware and Promox forums.

Their fix was to suppress the kernel warnings by adding the following as a boot parameter to the boot line in /etc/default grub:
```

split_lock_detect=off

```

---

