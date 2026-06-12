---
title: "[resolved] Ubuntu 22.04 Hanging - i915 - Xorg use a lot of CPU - fan problem"
date: 2023-02-25
forum: General Help
---

### Post by david3252 on 2023-02-25
Hello,
I have a problem on Ubuntu 22.04LTS. It is the same on the live USB 22.04 LTS. So I think it is not linked to my configuration.
Other people seem to have similar problem. A person on a Lenovo Yoga Slim 7 Pro 14IAP7 : [https://ubuntuforums.org/showthread.php?t=2483059](https://ubuntuforums.org/showthread.php?t=2483059)
I have a Lenovo Yoga 7i

I try many other no solution now :(

I make a bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2007853](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2007853)
With more information


Any one have an idea ?

Thanks in advance
David

---

### Post by DuckHook on 2023-02-25
Welcome to the forums, david3252

Please refrain from hijacking other forum member's threads. It deprives both you and them of the individualized focus that you both deserve.

Similar looking problems are most often due to unrelated causes. If you think that your problem is exactly the same as another member's, then it is acceptable to link to their thread in your own.

The OP included sufficient information, including logs and HW specs to work with. Your post is lacking in all detail, so it is impossible to know where to begin helping you. The Launchpad bug that you link to is also missing the critical log entries for proper triage.

I have split your post from the OP's and given it a new title. Hopefully, others will be able to help you.

---

### Post by david3252 on 2023-02-25
> **DuckHook said:**
> Welcome to the forums, david3252

Please refrain from hijacking other forum member's threads. It deprives both you and them of the individualized focus that you both deserve.

Similar looking problems are most often due to unrelated causes. If you think that your problem is exactly the same as another member's, then it is acceptable to link to their thread in your own.

The OP included sufficient information, including logs and HW specs to work with. Your post is lacking in all detail, so it is impossible to know where to begin helping you. The Launchpad bug that you link to is also missing the critical log entries for proper triage.

I have split your post from the OP's and given it a new title. Hopefully, others will be able to help you.

Ok I'm sorry. 
Thanks you

---

### Post by DuckHook on 2023-02-25
Post the relevant portions of your logs and we will see what we can do to help.

---

### Post by MAFoElffen on 2023-02-26
+1, but... Not just the portion of the logs...

Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") so we can see what your hardware is, how it is seen by Linux, and what your graphics configuration is. There is a comprehensive section in that report for graphics and the graphics layer. Please post the URL where it uploads the report to a pastebin.

---

### Post by david3252 on 2023-02-26
Hi this is my pastebin with Ubuntu 22.04 Live USB.
[https://pastebin.com/EzUk7r7V](https://pastebin.com/EzUk7r7V)

It is a fresh install with vlc and vmware and :
```

vdpau-driver-all est déjà la version la plus récente (1.4-3build2).
i965-va-driver est déjà la version la plus récente (2.4.1+dfsg1-1).
mesa-va-drivers est déjà la version la plus récente (22.2.5-0ubuntu0.1~22.04.1).
mesa-vdpau-drivers est déjà la version la plus récente (22.2.5-0ubuntu0.1~22.04.1).
intel-media-va-driver est déjà la version la plus récente (23.1.1+dfsg1-0ubuntu1~22.04.sav0).
libva-drm2 est déjà la version la plus récente (2.17.0-1~22.04.sav0).
libva-wayland2 est déjà la version la plus récente (2.17.0-1~22.04.sav0).
va-driver-all est déjà la version la plus récente (2.17.0-1~22.04.sav0).

```

Thanks

---

### Post by MAFoElffen on 2023-02-26
I see you are running Ubuntu 22.04.1 from a LiveCD image via USB port Port 1: Dev 2. I can see most of your hardware, except a very important factor... I do not see any of your internal storage. What does it have for internal storage and what is installed on it?

Ubuntu 22.04.1 is going to run slower from a LiveCD via USB then it is going to run if installed natively.

Please describe your problem in detail... How do you suspect that you are experiencing a high CPU load? How do you suspect that it is tied to the i915 driver?

---

### Post by david3252 on 2023-02-27
Hello,
Thanks !
I'm running from the LiveCD for this test, but it is the same on my installed Ubuntu. LiveCD is neutral so we are sure it is not my configuration file that make problem.
I have an nvme drive.

I'm on the 5.19.0-32-generic. I have just retry on an "old" 5.15 :  5.15.0-52, with the last 5.15.0-60 and with the last 6.1.0-1006oem. It  is the same, it crash the same.
The 5.15 kernel have better 3D hardware support with VMWare. The DirectX  diag with DirectX 7, 8, 9 work better. The cube is very fluid, it is  not the case with the 5.19 or 6.1
Don't know if driver have been modify.

For all cases the log is very poor ... (dmesg, syslog, Xorg)
```

 kernel: [   30.424697] x86/split lock detection: #AC: main-svga/3123 took a split_lock trap at address: 0x5621f30a2e3d
kernel: [   30.611750] x86/split lock detection: #AC: vmx-svga/3120 took a split_lock trap at address: 0x55ea598febb7
kernel: [   30.628239] x86/split lock detection: #AC: main-mks/3122 took a split_lock trap at address: 0x5621f30a30a7

kernel: [    0.000000] x86/split lock detection: #AC: crashing the  kernel on kernel split_locks and warning on user-space split_locks

```

Another time :
```

kernel: [   51.879397] split_lock_warn: 35 callbacks suppressed

```

It work very well until crash.

The problem is when I'm charging a lot or aleatory the graphic hang, lag, and be none fluid. ALT+TAB take a lot of time, changing tab on the system-monitor to. Changing to an open apps to an other to.
And Xorg take a lot of CPU, but not before. The "crash" is the starting point of lagging.
I show the slip lock when it crash but some time I have it without crash.

In a normal way the system is very quick and fluent on my nvme or on the USB Live.



I show this thing :
If I put in sleep the computer (after the lag begin), it work better after the sleep. If I  hibernate the computer sometime its works like before the bug or  minimally better than before hibernation.

A people deal with a lost of sync in an other topic or forum, it could  be that. I think sleep or hibernate have only impact on the hardware.

The better effect I can measure is the interrupts :
Before the bug :
```

cat /proc/interrupts :  
150:          0      12500          0          0          0          0           0          0  IR-PCI-MSI 327680-edge      xhci_hcd
 130:          0          0         36          0          0          0           0          0  IR-PCI-MSI 212992-edge      xhci_hcd
 195:          0          0          0        765          0          0      43917          0  IR-PCI-MSI 32768-edge      i915

 NMI:          3          3          2          3          1          1          2          1   Non-maskable interrupts
 LOC:      44084      45148      38917      43380      44347      39950      63891      41043   Local timer interrupts
 SPU:          1          0          0          0          0          0          0          0   Spurious interrupts
 PMI:          3          3          2          3          1          1           2          1   Performance monitoring interrupts
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
 150:       7011      37888          0          0          0          0           0      10041  IR-PCI-MSI 327680-edge      xhci_hcd
 130:         10          0         36          0          0          0           0          9  IR-PCI-MSI 212992-edge      xhci_hcd

 NMI:          4          6          6          4          1          1          4          3   Non-maskable interrupts
 LOC:     460124     453153     482067     473181     455918     460154     609368     463418   Local timer interrupts
 SPU:          1          0          0          0          0          0          0          0   Spurious interrupts
 PMI:          4          6          6          4          1          1           4          3   Performance monitoring interrupts
 IWI:      28098      23300      16538      19575      21421      22590     505527      24870   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:      23455      16173      11638      19702      12745      12816      11421      15952   Rescheduling interrupts
 CAL:     131999     114719     106123      98885     108117     112193     110945     100299   Function call interrupts
 TLB:      28703      24931      27732      24161      29120      27679      33927      25081   TLB shootdowns
 **TRM:      18027      18039      18034      18040      18039      18038      18027      18032   Thermal event interrupts**

```
What deal with Thermal event interrupts ?


I'm show lot of problem this i915 so I made the problem on it, but it could by on mesa. I thinks intel-va-driver is not in the kernel. Here we see the but not depend on the kernel, so it is not depending to the drivers include in kernel ?

---

### Post by MAFoElffen on 2023-02-27
*** Please go back to the last post and use Edit > Advanced > Select each text of ouput to highlight. Then use the '#' Icon to wrap the outputs in CODE Tags. Do that for Raw Out or Commands in posts. It is easier to read, and... if not, it cause havoc with the Forums Software.

The problem is with the vmx-svga module. When Virtual Machines are running and the CPU tries to do a split lock, then, when monitored the log fills up with warnings. This happens most frequent when 3D Acceleration is used. This is a reported problem / bug in VMware. I see VirtualBox has the same module(?)

The current fix is to use the Linux kernel boot parameter
```

split_lock_detect=off

```
in the boot line in /etc/default/grub, then do 'update-grub'... to turn off split lock detection. This seems to fix that.

---

### Post by david3252 on 2023-02-27
Thanks a lot, I will try :)

---

### Post by MAFoElffen on 2023-02-27
A good place for it is directly after "boot splash"

---

### Post by david3252 on 2023-02-28
Thanks, I put it at the end of : GRUB_CMDLINE_LINUX_DEFAULT=
It seem to work : kernel: [    1.505914]     split_lock_detect=off

VMWare is fluid like with 5.15 kernel but it crash to :( !
Nothing on log, so the slip_off is really disable.

It seem to be better, it is more usable, but it is very slow.

It seem to be better on interrupt :
```

 149:          0          0          0          0          0          0          0         36  IR-PCI-MSI 212992-edge      xhci_hcd
 150:          0          0      18438          0          0     107602          0          0  IR-PCI-MSI 327680-edge      xhci_hcd
 195:          0          0          0       2465          0          0     298586          0  IR-PCI-MSI 32768-edge      i915
 NMI:          0          0          0          2          0          0          2          0   Non-maskable interrupts
 LOC:     153476     132417     138392     132333     113106     129923     114188     126213   Local timer interrupts
 SPU:          1          0          0          0          0          0          0          0   Spurious interrupts
 PMI:          0          0          0          2          0          0          2          0   Performance monitoring interrupts
 IWI:      20615      19155      13095      20396      17378      15499     164760      18339   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:       4072       3813       4495       4577       4197       3794       4345       4237   Rescheduling interrupts
 CAL:      45781      34113      44527      29049      27160      31731      30410      39933   Function call interrupts
 TLB:        505        951       2064        645        991        755        525        439   TLB shootdowns
** TRM:       7777       7774       7781       7779       7781       7781       7777       7779   Thermal event interrupts**
 THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
```

Less than 8000, before it was 18000 for Thermal event interrupts

My computer make hissing (electronic noize) when the bug start. It is not the fan, it is an electronic sound like a PWM chopper.
So the concept of lost of synchronization is possible for me.


After sleeping :
```

 149:         28          0          0          0          0          0          0         43  IR-PCI-MSI 212992-edge      xhci_hcd
 150:      14273          0      18438          0          0     107997          0      32359  IR-PCI-MSI 327680-edge      xhci_hcd
 195:       5107          0          0       2465          0          0     578525          0  IR-PCI-MSI 32768-edge      i915
NMI:          0          5          4          6          4          4          5          4   Non-maskable interrupts
 LOC:     266036     233291     225858     224141     201968     225313     275404     228301   Local timer interrupts
 SPU:          1          0          0          0          0          0          0          0   Spurious interrupts
 PMI:          0          5          4          6          4          4          5          4   Performance monitoring interrupts
 IWI:      30531      26572      17767      26939      23038      23128     300892      25938   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:       4919       4808       5299       5368       5014       4734       5374       5258   Rescheduling interrupts
 CAL:      90652      71970      77649      64670      57497      65106      63732      72078   Function call interrupts
 TLB:      23736      25685      26150      27891      23610      26219      24274      23895   TLB shootdowns
** TRM:      10099      10096      10103      10101      10103      10103      10099      10101   Thermal event interrupts**
 THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
 DFR:          0          0          0          0          0          0          0          0   Deferred Error APIC interrupts
 MCE:          0          0          0          0          0          0          0          0   Machine check exceptions
 MCP:         10         10         10         10         10         10         10         10   Machine check polls

```

After hybernation :
```

149:          0          0          0          0         26          0          0          0  IR-PCI-MSI 212992-edge      xhci_hcd
170:          0          0          0          0          0       7469          0        161  IR-PCI-MSI 327680-edge      xhci_hcd
195:      33116          0          0       2465          0          0     590987          0  IR-PCI-MSI 32768-edge      i915
 NMI:          0          5          4          6          4          4          5          4   Non-maskable interrupts
 LOC:     286938     246203     237547     236966     213287     238352     291710     242038   Local timer interrupts
 SPU:          1          0          0          0          0          0          0          0   Spurious interrupts
 PMI:          0          5          4          6          4          4          5          4   Performance monitoring interrupts
 IWI:      43679      27741      18651      27982      23621      24348     307196      27273   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:       5055       4895       5409       5632       5138       4820       5480       5355   Rescheduling interrupts
 CAL:      93539      73742      78954      65890      58589      66252      64810      73193   Function call interrupts
 TLB:      23839      25908      26263      28107      23749      26286      24387      24031   TLB shootdowns
** TRM:      10368      10338      10372      10370      10372      10372      10368      10370   Thermal event interrupts**
 THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
 DFR:          0          0          0          0          0          0          0          0   Deferred Error APIC interrupts
 MCE:          0          0          0          0          0          0          0          0   Machine check exceptions
 MCP:         12         12         12         12         12         12         12         12   Machine check polls

```


Do you have any news idea ?
Thanks in advance
David

---

### Post by david3252 on 2023-02-28
I don't found anything dealing with Thermal event interrupts. I found this [https://patchwork.kernel.org/project/linux-pm/patch/20220106025059.25847-6-ricardo.neri-calderon@linux.intel.com/](https://patchwork.kernel.org/project/linux-pm/patch/20220106025059.25847-6-ricardo.neri-calderon@linux.intel.com/) could it be a begin of an answer ?

---

### Post by MAFoElffen on 2023-02-28
I did find an Ubuntu Bug and corresponding VMware Workstation Bug with Ubuntu and Linux Kernel 5.15... Not exactly the same as yours as they are having booting problems.

They turned off Wayland in /etc/gdm3/custom.conf by uncommenting WaylandEnable=false.

Then using boot parameter "acpi=force"...

Still looking...

---

### Post by ActionParsnip on 2023-02-28
Do you have the latest BIOS? It may help

---

### Post by david3252 on 2023-02-28
> **MAFoElffen said:**
> I did find an Ubuntu Bug and corresponding VMware Workstation Bug with Ubuntu and Linux Kernel 5.15... Not exactly the same as yours as they are having booting problems.

They turned off Wayland in /etc/gdm3/custom.conf by uncommenting WaylandEnable=false.

Then using boot parameter "acpi=force"...

Still looking...

Thanks, VMWare help to crash but is not the only one. With VMWare is about 100% crash with DirectX test so it is easier to test configuration. 
Today I'm just going on internet with Firefox and a video on incrustation, and the crash start ! It is longer to append with Firefox. I have enable hardware GPU acceleration on Firefox.

I have Mate, it's no compatible with Wayland.

I will try acpi=force 


> **ActionParsnip said:**
> Do you have the latest BIOS? It may help

Thanks, yes I have already done. After I found Lenovo make a tool on  Linux to check all possible firmware upgrade for computer, and if it  work, all of my hardware is up to date.

---

### Post by david3252 on 2023-02-28
acpi=force stay the same.
I just try with cinnamon and it is the same :(
The test on the LiveUSB is on gnome so probably with wayland.

---

### Post by david3252 on 2023-08-21
Hello !
Thanks to all, I have solution the problem !

The problem is purely hardware. My computer have a problem and the technician have forgot to plug the fan connector.
With Intel® Turbo Boost Technology and the built-in thermal protection, it is very difficult to found thermal problem. The computer never turn off, but turn at very low speed.
I'm think it would be the same for an old thermal pad or an old thermal past.
The CPU reduce the frequency to reduce temperature. My laptop case is metallic, so it participate to evacuate the warm.

[https://www.intel.com/content/www/us/en/support/articles/000060293/processors.html](https://www.intel.com/content/www/us/en/support/articles/000060293/processors.html)
[https://www.intel.com/content/www/us/en/support/articles/000005597/processors.html](https://www.intel.com/content/www/us/en/support/articles/000005597/processors.html)

Today with the fan correctly plug, I don't have Thermal event interrupts. So I think it is the only way to check a bad thermal pad, or a defective cpu fan when the computer, like me, doesn't monitor it !

Have a good day !

---

