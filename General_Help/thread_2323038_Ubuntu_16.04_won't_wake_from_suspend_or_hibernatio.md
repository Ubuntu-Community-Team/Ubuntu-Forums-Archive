---
title: "Ubuntu 16.04 won't wake from suspend or hibernation, and will not shut down."
date: 2016-05-02
forum: General Help
---

### Post by Mark1119 on 2016-05-02
I'm running Ubuntu 16.04 on a Dell 15z 5523 - fresh install. Whenever I close the laptop's lid, the computer will not wake from suspend and I am forced to shut the computer down to reuse it. The only way to shut down the computer is a long-hold on the power button. Telling the system to shut down from within the OS will not work. When I initiate shutdown from the OS, the process hangs at the splash screen. I had the same problem in 14.04, and I thought upgrading might fix my problem. Unfortunately, it has not. Any ideas?

---

### Post by gnusci on 2016-05-02
Post the info of following commands:

lspci -nn | egrep "VGA|Display" 

sudo lshw -C display

---

### Post by Mark1119 on 2016-05-02
For "[COLOR=#000000]lspci -nn | egrep "VGA|Display" ":[/COLOR]

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)

and for "sudo lshw -C display":



  *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:25 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)




Thank you!

---

### Post by bluepicaso2 on 2016-05-03
> **gnusci said:**
> Post the info of following commands:

lspci -nn | egrep "VGA|Display" 

sudo lshw -C display

I am on Lenovo Ideadpad 300, same problem with 16.04.
output for [B]lspci -nn | egrep "VGA|Display" 

[/B]```

00:02.0 VGA compatible controller [0300]: Intel Corporation Sky Lake Integrated Graphics [8086:1916] (rev 07)
03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330] [1002:6660] (rev ff)

```

Output for [B]sudo lshw -C display
[/B]```
This command just freezes no output
```
I guess this is realted to other issue where lsusb is also stuck with no output.
Help me if you could.

---

### Post by bluepicaso2 on 2016-05-04
The solution was to update kernel to 4.4.8. And suspend and resume on laptop worked like a charm.
[http://www.ubuntumaniac.com/2016/04/update-upgrade-linux-kernel-448-lts-on.html](http://www.ubuntumaniac.com/2016/04/update-upgrade-linux-kernel-448-lts-on.html)

---

### Post by Mark1119 on 2016-05-04
You had the same shut down and suspend issue and it fixed both?

---

### Post by bluepicaso2 on 2016-05-04
> **Mark1119 said:**
> You had the same shut down and suspend issue and it fixed both?

I did not shut down since morning. But my shut down had been working fine mostly. 
Suspend had fixed. Previsouly, when i did suspend (with laptop lid closed and from menu) the screen tuned off, but syestm did not go to suspend state. The only way was to hard restart.
After kernel update  this was solved.
PLUS (for me) auto detection for mobile broadband also worked like a charm.

---

### Post by Mark1119 on 2016-05-04
I see. I upgraded the kernel for good measure and it made no difference. Thanks for the suggestion though.

---

### Post by hamlet32 on 2016-05-17
i too had the same problem of not suspending on closing thee lid requiring a hard reset every time. i am on Lenovo G40. upgrading the kernel to 4.4.8 as suggested by bluepicaso2 solvedd the problem.
thanks

---

### Post by Mark1119 on 2016-05-25
Upgrading the kernel made no difference for me. Any suggestions?

---

### Post by tsayers69 on 2016-09-08
Hi Folks, 
I am hoping someone can provide some guidance. 

I have a lenovo z710 and like others it will not wake up from suspend.  I love Ubuntu and have been an avid user since version 4-5.  If there is one feature I use and depend on it is suspend as it allows me to continue working from where I left off.  There seams to be a lot of churn out there regarding this topic for many months on 16 and years with other versions.

I have tried everything in all the blogs I have found, different driver, upgraded to 4.4.8 kernel,... to no avail.

Any assistance would be greatly appreciated.

I am getting messages during boot and not sure if they are related to the suspend/wake issue.

Error parsing PPC subspaces from PPCT
nouveau DRM: pointer to TMDS table invalid
nouveau DRM: pointer to flat panel table invalid

Here is requested output 
lspci -nn | egrep "VGA|Display" 
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)

 sudo lshw -C display
  *-display               
       description: 3D controller
       product: GK107M [GeForce GT 745M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:29 memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:d1000000-d13fffff memory:c0000000-cfffffff ioport:5000(size=64)

---

