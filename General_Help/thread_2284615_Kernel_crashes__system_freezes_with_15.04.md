---
title: "Kernel crashes / system freezes with 15.04"
date: 2015-06-30
forum: General Help
---

### Post by juha-e on 2015-06-30
Hi,

I'm bit in a loss here as where to start digging into this problem. Since upgrade from 14.10 to 15.04 I'm getting frequent total system lock-ups on Acer Travelmate B115-M laptop.

14.10 did run like a charm with no issues - these crashes have started with upgrade. I've installed OpenSuSE Tumbleweed on this same hardware to verify that the hardware is working and it runs without crashes. Proves nothing of course, but I used it for weeks with similar software setup without an issue.

These lock-ups happen when entering sleep mode by closing laptop lid. System does not enter sleep mode. At that point there will be frozen lock screen on the display and nothing else will happen. No reaction to sysrq keys (nothing gets written in log file at least), only way to recover is force power off and reboot. This was annoyingly frequent just after the distribution upgrade and seems to happen now less frequently (2-3 times a week perhaps).

Any suggestions to narrow this down? I'd suspect buggy broadcom or chipset driver (or combination?) based on the log entries.

juhas@laphroaig:/proc$ lscpu 
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 55
Model name:            Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz
Stepping:              8
CPU MHz:               499.741
CPU max MHz:           2665,6001
CPU min MHz:           499,8000
BogoMIPS:              4326.40
Virtualization:        VT-x
L1d cache:             24K
L1i cache:             32K
L2 cache:              1024K
NUMA node0 CPU(s):     0-3

juhas@laphroaig:/proc$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
00:13.0 SATA controller: Intel Corporation Device 0f23 (rev 0e)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series USB xHCI (rev 0e)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0e)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation Device 0f48 (rev 0e)
00:1c.1 PCI bridge: Intel Corporation Device 0f4a (rev 0e)
00:1c.2 PCI bridge: Intel Corporation Device 0f4c (rev 0e)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation Device 0f12 (rev 0e)
02:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)


Attached couple of snips from logs which are last things written during crash happens. Similar errors seem to be present from succesful sleep/wakeup cycles so these do not necessarily show the failure.

Update: Fixed the most visible error with missing bluetooth firmware (however bluetooth worked just fine in that state), so overall less errors in log now. Already hoped it had fixed it, but today again full lockup when entering sleep. Nothing happens with sysrq keys, system is totally freezed :( 

Latest log entry added below, that is from time of closing the lid and then nothing happens. Based on log, that looks like a instant resume after sleep for some reason and no failures whatsoever visible. What should I do next? If it's usb related (that internal broadcom bluetooth is usb), then in theory it's possible that keyboard is totally lost? Haven't yet tried to ssh from another box to see if there is any life left.

juhas@laphroaig:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c57 Sunplus Innovation Technology Inc. 
Bus 001 Device 005: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0489:e046 Foxconn / Hon Hai 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


snip:

Jul  9 09:53:33 laphroaig kernel: [129107.427423] done.
Jul  9 09:53:33 laphroaig kernel: [129107.427433] PM: Preparing system for mem sleep
Jul  9 09:53:33 laphroaig kernel: [129107.427663] Freezing user space processes ... (elapsed 0.139 seconds) done.
Jul  9 09:53:33 laphroaig kernel: [129107.567578] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Jul  9 09:53:33 laphroaig kernel: [129107.569416] PM: Entering mem sleep
Jul  9 09:53:33 laphroaig kernel: [129107.569438] Suspending console(s) (use no_console_suspend to debug)
Jul  9 09:53:33 laphroaig kernel: [129107.585680] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jul  9 09:53:33 laphroaig kernel: [129107.586022] sd 0:0:0:0: [sda] Stopping disk
Jul  9 09:53:33 laphroaig kernel: [129108.183888] PM: suspend of devices complete after 613.669 msecs
Jul  9 09:53:33 laphroaig kernel: [129108.207770] PM: late suspend of devices complete after 23.843 msecs
Jul  9 09:53:33 laphroaig kernel: [129108.208450] r8169 0000:03:00.0: System wakeup enabled by ACPI
Jul  9 09:53:33 laphroaig kernel: [129108.208706] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
Jul  9 09:53:33 laphroaig kernel: [129108.222912] PM: noirq suspend of devices complete after 15.122 msecs
Jul  9 09:53:33 laphroaig kernel: [129108.222957] ACPI: Preparing to enter system sleep state S3
Jul  9 09:53:33 laphroaig kernel: [129108.223302] PM: Saving platform NVS memory
Jul  9 09:53:33 laphroaig kernel: [129108.223333] Disabling non-boot CPUs ...
Jul  9 09:53:33 laphroaig kernel: [129108.223390] intel_pstate CPU 1 exiting
Jul  9 09:53:33 laphroaig kernel: [129108.224795] kvm: disabling virtualization on CPU1
Jul  9 09:53:33 laphroaig kernel: [129108.224820] smpboot: CPU 1 is now offline
Jul  9 09:53:33 laphroaig kernel: [129108.225423] intel_pstate CPU 2 exiting
Jul  9 09:53:33 laphroaig kernel: [129108.226790] kvm: disabling virtualization on CPU2
Jul  9 09:53:33 laphroaig kernel: [129108.226837] smpboot: CPU 2 is now offline
Jul  9 09:53:33 laphroaig kernel: [129108.227354] intel_pstate CPU 3 exiting
Jul  9 09:53:33 laphroaig kernel: [129108.227627] Broke affinity for irq 17
Jul  9 09:53:33 laphroaig kernel: [129108.227705] Broke affinity for irq 261
Jul  9 09:53:33 laphroaig kernel: [129108.227707] Broke affinity for irq 262
Jul  9 09:53:33 laphroaig kernel: [129108.228741] kvm: disabling virtualization on CPU3
Jul  9 09:53:33 laphroaig kernel: [129108.228765] smpboot: CPU 3 is now offline
Jul  9 09:53:33 laphroaig kernel: [129108.229607] ACPI: Low-level resume complete
Jul  9 09:53:33 laphroaig kernel: [129108.229675] PM: Restoring platform NVS memory
Jul  9 09:53:33 laphroaig kernel: [129108.230259] Enabling non-boot CPUs ...
Jul  9 09:53:33 laphroaig kernel: [129108.230316] x86: Booting SMP configuration:
Jul  9 09:53:33 laphroaig kernel: [129108.230318] smpboot: Booting Node 0 Processor 1 APIC 0x2
Jul  9 09:53:33 laphroaig kernel: [129108.246062] kvm: enabling virtualization on CPU1
Jul  9 09:53:33 laphroaig kernel: [129108.248552] CPU1 is up
Jul  9 09:53:33 laphroaig kernel: [129108.248586] smpboot: Booting Node 0 Processor 2 APIC 0x4
Jul  9 09:53:33 laphroaig kernel: [129108.264328] kvm: enabling virtualization on CPU2
Jul  9 09:53:33 laphroaig kernel: [129108.266768] CPU2 is up
Jul  9 09:53:33 laphroaig kernel: [129108.266806] smpboot: Booting Node 0 Processor 3 APIC 0x6
Jul  9 09:53:33 laphroaig kernel: [129108.282549] kvm: enabling virtualization on CPU3
Jul  9 09:53:33 laphroaig kernel: [129108.285095] CPU3 is up
Jul  9 09:53:33 laphroaig kernel: [129108.285553] ACPI: Waking up from system sleep state S3
Jul  9 09:53:33 laphroaig kernel: [129108.404016] acpi LNXPOWER:00: Turning OFF
Jul  9 09:53:33 laphroaig kernel: [129108.420063] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
Jul  9 09:53:33 laphroaig kernel: [129108.420347] PM: noirq resume of devices complete after 16.304 msecs
Jul  9 09:53:33 laphroaig kernel: [129108.452503] PM: early resume of devices complete after 32.059 msecs
Jul  9 09:53:33 laphroaig kernel: [129108.453295] r8169 0000:03:00.0: System wakeup disabled by ACPI
Jul  9 09:53:33 laphroaig kernel: [129108.453317] rtc_cmos 00:00: System wakeup disabled by ACPI
Jul  9 09:53:33 laphroaig kernel: [129108.471674] sd 0:0:0:0: [sda] Starting disk
Jul  9 09:53:33 laphroaig kernel: [129108.728809] usb 1-2: reset high-speed USB device number 2 using xhci_hcd
Jul  9 09:53:33 laphroaig kernel: [129108.857437] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88017989a420
Jul  9 09:53:33 laphroaig kernel: [129108.969036] usb 1-4: reset high-speed USB device number 3 using xhci_hcd
Jul  9 09:53:33 laphroaig kernel: [129109.209546] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88017989aa20
Jul  9 09:53:33 laphroaig kernel: [129109.225219] usb 1-2.3: reset full-speed USB device number 5 using xhci_hcd
Jul  9 09:53:33 laphroaig kernel: [129109.313928] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88017a065c60
Jul  9 09:53:33 laphroaig kernel: [129109.313931] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88017a065c00
Jul  9 09:53:33 laphroaig kernel: [129109.385459] usb 1-2.1: reset full-speed USB device number 4 using xhci_hcd
Jul  9 09:53:33 laphroaig kernel: [129109.474631] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88003e4e0d00
Jul  9 09:53:33 laphroaig kernel: [129109.474633] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88003e4e0d90
Jul  9 09:53:33 laphroaig kernel: [129109.474635] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88003e4e0d48
Jul  9 09:53:33 laphroaig kernel: [129109.474638] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88003e613dc8
Jul  9 09:53:33 laphroaig kernel: [129109.474640] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88003e613d80
Jul  9 09:53:33 laphroaig kernel: [129109.474642] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88003e613d08
Jul  9 09:53:33 laphroaig kernel: [129109.474644] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88003e613cc0
Jul  9 09:53:33 laphroaig kernel: [129109.476614] PM: resume of devices complete after 1023.288 msecs
Jul  9 09:53:33 laphroaig kernel: [129109.478919] PM: Finishing wakeup.
Jul  9 09:53:33 laphroaig kernel: [129109.478923] Restarting tasks ... 
Jul  9 09:53:33 laphroaig kernel: [129109.492149] Bluetooth: hci0: BCM: patching hci_ver=06 hci_rev=1000 lmp_ver=06 lmp_subver=220e
Jul  9 09:53:33 laphroaig kernel: [129109.520650] done.
Jul  9 09:53:33 laphroaig kernel: [129109.543286] r8169 0000:03:00.0 eth0: link down
Jul  9 09:53:33 laphroaig kernel: [129110.125961] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=152f lmp_ver=06 lmp_subver=220e
Jul  9 09:53:34 laphroaig kernel: [129110.481579] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul  9 09:53:34 laphroaig kernel: [129110.598874] ata1.00: configured for UDMA/133
Jul  9 09:53:39 laphroaig kernel: [129115.930778] IPv6: wlan0: IPv6 duplicate address fe80::a3e:8eff:fef1:e45b detected!

---

### Post by ckrzen on 2015-08-28
I had the same problem on my DELL Inspiron 3646 BIOS ver. A08 using an Intel(R) Pentium(R) CPU  J2900  @ 2.41GHz.

My solution, so far, with kernel:  3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:32 UTC 2015 x86_64:

add:  intel_pstate=disable to the kernel boot cmdline:

BOOT_IMAGE=/boot/vmlinuz-3.19.0-26-generic.efi.signed root=UUID=5ab2d1c9-0f00-470c-9292-58387a5cd983 ro quiet intel_pstate=disable


Hope this helps!



*** UPDATE:

It turns-out that my problem is more related to the "Bay Trail / ValleyView" graphics stack in the stock 15.04 release. I've reinstalled and left the "pstate" driver enabled, per default, in kernel.

I've updated to DELL BIOS code ver:  A09


I'm having good results applying the following ideas, in order:



[SIZE=5]**ALREADY TRIED:**[/SIZE]


Add "i915.semaphores=1" to /etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.semaphores=1"
```

followed by:

```
$sudo update-grub
```


ALSO:  disable VTd(Intel Virtualization Technologies) in the BIOS for increased stability




[SIZE=5]**NOT TRIED:**[/SIZE]


/etc/X11/xorg.conf.d/20-intel.conf
 Section "Device"
    Identifier "old intel stuff"
    Driver "intel"
    Option "Shadow" "True"
    Option "DRI" "false"
 EndSection


Add the following to GRUB_CMDLINE_LINUX in /etc/default/grub:

drm.debug=0 drm.vblankoffdelay=1 i915.semaphores=0 i915.modeset=1 i915.use_mmio_flip=1 i915.powersave=1 i915.enable_ips=1 i915.disable_power_well=1 i915.enable_hangcheck=1 i915.enable_cmd_parser=1 i915.fastboot=0 i915.enable_ppgtt=1 i915.reset=0 i915.lvds_use_ssc=0 i915.enable_psr=0


X freeze/crash with intel driver

Some issues with X crashing, GPU hanging, or problems with X freezing, can be fixed by disabling the GPU usage with the NoAccel option:

/etc/X11/xorg.conf.d/20-intel.conf

Section "Device"
   Identifier "Intel Graphics"
   Driver "intel"
   Option "NoAccel" "True"
EndSection

Alternatively, try to disable the 3D acceleration only with the DRI option:

/etc/X11/xorg.conf.d/20-intel.conf

Section "Device"
   Identifier "Intel Graphics"
   Driver "intel"
   Option "DRI" "False"
EndSection


/usr/share/X11/xorg.conf.d/20-intel.conf:

Code:
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection



grub:

intel_pstate=disable

---

### Post by juha-e on 2015-10-27
Thanks for the reply!

Anyway, I didn't have time to fiddle around with this much and got bored of crashes, so I've been now running 15.10 for a while - and that seems to run ok. At least so far so good.

---

### Post by juha-e on 2015-11-17
Actually not ok. Crashes happen also with 15.10, but in different form. Perhaps a different issue, but crashes do now happen "in-use" and not related to sleep any more. Full lock-ups in X when just browsing or doing something else. Nothing gets written to logs. Damn this.

---

### Post by juha-e on 2015-12-06
Ok, root cause has been pointed to i915 driver and it seems to affect quite a number of systems (Baytrail).

Bug and workaround for it is described here. [https://bugs.freedesktop.org/show_bug.cgi?id=88012](https://bugs.freedesktop.org/show_bug.cgi?id=88012)

So either 3.16.7 or earlier kernel works or using [COLOR=#000000]"intel_idle.max_cstate=1" option with newer kernels (I've tried upto  4.3.0 now) this runs now stable.[/COLOR]

---

