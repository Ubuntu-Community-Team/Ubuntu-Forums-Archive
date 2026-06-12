---
title: "PC freezes occasionally"
date: 2022-02-10
forum: General Help
---

### Post by satimis on 2022-02-10
Hi all,

My PC freezes occasionally.  I have to press hard-reset button to restart it.  I couldn't predict when it will happen.

$ lscpu > lscpu.txt
(lscpu.txt file attached)

$ free -m```

              total        used        free      shared  buff/cache   available
Mem:          30063        2448       25031         156        2583       27028
Swap:           975           0         975

```

Please advise where I have to check and how to fix the problem?

Thanks

Regards

---

### Post by linux-sysop on 2022-02-10
I always assume hardware is first at fault.  I recommend you eliminate any hardware issues by running a Live boot for at least 8 to 12 hours. If you can do that without freezing up, then it is a software error.  

If you ran without issue on a Live boot, the next step is killing all the processes that start up by timers.  

Wait for the next lockup and perform a  REISUB.

Hold ALT+SysReq (on Print Screen key) and type R, E, I, S, U, B

R:  Switch to XLATE mode
E:  Send Terminate signal to all processes except for init
I:  Send Kill signal to all processes except for init
S:  Sync all mounted file-systems
U:  Remount file-systems as read-only
B:  Reboot

That is less harsh than cold booting.

If you still have keyboard on lockup, you can try ALT+F2  or CTRL+ALT+F1 to get access to programs.  It will be difficult in any case to find the fault in the software.  I would start in the power management and go from there.

**Note:** If REISUB doesn't work, you might try FN key in place of ALT.

---

### Post by satimis on 2022-02-10
> **linux-sysop said:**
> I always assume hardware is first at fault.  I recommend you eliminate any hardware issues by running a Live boot for at least 8 to 12 hours. If you can do that without freezing up, then it is a software error.  

If you ran without issue on a Live boot, the next step is killing all the processes that start up by timers.  

Wait for the next lockup and perform a  REISUB.

Hold ALT+SysReq (on Print Screen key) and type R, E, I, S, U, B

R:  Switch to XLATE mode
E:  Send Terminate signal to all processes except for init
I:  Send Kill signal to all processes except for init
S:  Sync all mounted file-systems
U:  Remount file-systems as read-only
B:  Reboot

That is less harsh than cold booting.

If you still have keyboard on lockup, you can try ALT+F2  or CTRL+ALT+F1 to get access to programs.  It will be difficult in any case to find the fault in the software.  I would start in the power management and go from there.

**Note:** If REISUB doesn't work, you might try FN key in place of ALT.
Thanks for your advice.

According to my recollection the lockup happened on Internet browsing on Firefox/Chrome.

The power supply is a brand-new unit, Corair CX550M 550 Watts.   I just changed it about one month ago.  This PC has been running about 3/4 years.  Lockup just happened.

I'll wait for next lockup to test your advice.

Regards

---

### Post by naxal on 2022-02-10
Hello,

>  This PC has been running about 3/4 years. Lockup just happened.

Apart from suspending the PSU, keep an eye on your CPU / GPU Temps also. If things are not clean in this many years, stuff can become dusty and thus blocking air flow or trapping heat.

Some time just removing the RAM & GPU, cleaning the slot and then putting it back helps to solve all these issues.

Thanks.

---

### Post by satimis on 2022-02-10
> **naxal said:**
> Hello,



Apart from suspending the PSU, keep an eye on your CPU / GPU Temps also. If things are not clean in this many years, stuff can become dusty and thus blocking air flow or trapping heat.

Some time just removing the RAM & GPU, cleaning the slot and then putting it back helps to solve all these issues.

Thanks.
Hi,

Thanks for your advice.

I'll wait for next lockup running linux-sysop's advice to check the PC.

The PC has been thoroughly cleaned when I installed the new Corsair powder supply a month ago, including CPU cooling fan.  I have been planning building a new AMD Ryzen 7 PC with 64G RAM sometimes.  Unfortunately I couldn't find spare time to do it.

Regards

---

### Post by Autodave on 2022-02-10
Do a RAM test.  If you have more than one RAM stick, remove all but one and try.  If good, replace that "good" one with another stick.  Repeat.  If you only get the lockup with one particular stick, that's your bad one.  

Remove any USB hubs.....especially powered ones.

Don't assume that the new PSU can't possibly be the problem.

---

### Post by satimis on 2022-02-10
> **Autodave said:**
> Do a RAM test.  If you have more than one RAM stick, remove all but one and try.  If good, replace that "good" one with another stick.  Repeat.  If you only get the lockup with one particular stick, that's your bad one.  
I'll check it.  2 RAM sticks - 2 x 16G= 32G 

> 
Remove any USB hubs.....especially powered ones.

Whether you meant the devices connected to USB ports?  Only loudspeaker and wireless keyboard/mouse receiver are connected to USB ports, no other device.

> 
Don't assume that the new PSU can't possibly be the problem.
I'll connect the old Corsair power supply back.  I connected the new Corsair power supply to test a 4K graphic card.  After the test I just left it there.  The old Corsair power supply was working without problem.

Regards

---

### Post by Autodave on 2022-02-10
What GPU?  Some of these new ones take a tremendous amount of power....a ridiculous amount.  Does the new GPU also take additional hook up for power?  If so, make sure that they are securely connected.

---

### Post by satimis on 2022-02-10
> **Autodave said:**
> What GPU?  Some of these new ones take a tremendous amount of power....a ridiculous amount.  Does the new GPU also take additional hook up for power?  If so, make sure that they are securely connected.

Graphic comes from AMD CPU

$ cat /proc/cpuinfo > cpuinfo.txt
(cpuinfo.txt attached)

$ sudo lshw -C display```

  *-display                 
       description: VGA compatible controller
       product: Picasso
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:08:00.0
       version: c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: driver=amdgpu latency=0
       resources: irq:91 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fcd00000-fcd7ffff

```

Regards

---

