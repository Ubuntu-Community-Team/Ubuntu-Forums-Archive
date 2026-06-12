---
title: "[SOLVED] no sound with compiled kernel"
date: 2008-02-15
forum: General Help
---

### Post by jjalocha on 2008-02-15
My new notebook is very unfriendly with Linux, and I had to recompile the kernel in order to get wi-fi working. Wifi seems to work now, but sound (which worked perfectly) disappeared completely!

```

$ aplay -l
aplay: device_list:204: no soundcards found...

```

This is the first time I compiled something, and I really don't have a clue where to look for the answer... Anyone with more experience who can guide me, please?

It is an Everex StepNote SA2053T notebook, with the following soundcard:

```

00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)

```

The procedure for compiling the kernel was, in short:

```

$ sudo apt-get install build-essential kernel-package linux-source
$ sudo cp /boot/config-`uname -r` .config
$ sudo make oldconfig
$ sudo make xconfig
# make-kpkg clean
# make-kpkg --initrd --revision=686 kernel_image kernel_headers modules_image
$ sudo dpkg -i linux*2.6.22*.deb
$ sudo shutdown -r now

```

I only made three changes to the kernel:

```

Device Drivers
> Network device support
> Ethernet (10 or 100Mbit)
> EISA, VLB, PCI and on board controllers
> RealTek RTL-8129/8130/8139 PCI Fast Ethernet Adapter support
> Use PIO instead of MMIO
# doesn't even boot if MMIO enabled

Device Drivers
> MMC/SD/SDIO support, can only select one arch from MMC and MSS
> MMC/SD card support (disable)
# this hangs the notebook

Processor type and features
> Core 2/newer Xeon (MCORE2)
# I suppose better performance for Pentium Dual Core

```

This notebook seems to be very similar to other Everex StepNote 205?T models, as well as Averatec 2460, Twinhead Stylebook H12Y, and the Philips Freevents x5? line. All information on the web talks about recompiling the kernel for solving the many problems. There are also some long-standing bugs in Ubuntu involved:
[LIST]
[*][installation guide for SA2053T]("http://www.poplarware.com/everexlinux.html")
[*][Laptop Testing Team Wiki for SA2053]("https://wiki.ubuntu.com/LaptopTestingTeam/EverexStepNoteSA2053T")
[*][Bug #187671: sdhci module hangs Everex StepNote 2053T]("https://bugs.launchpad.net/linux/+bug/187671")
[*][Bug #34902: Ralink Wireless legacy drivers (rt2500 rt61 rt73 rt2570) USB/PCMCIA/PCI hangs PC]("https://bugs.launchpad.net/ubuntu/+bug/34902")
[/LIST]

---

### Post by mbeierl on 2008-02-15
You had sound in the old kernel?  What's the output of lsmod?  What has probably happened is that the module for your sound card has not been built/loaded in your new kernel.

---

### Post by jjalocha on 2008-02-15
Yes, mbeierl, I think you're right. I rebooted with the old kernel, and found out that the driver used was 'snd_hda_intel'. For some reason, there is no such module available in the new kernel (doesn't appear with 'modprobe snd-[TAB]').

I don't understand why there seem to be no modules related to sound in the new build... But I will try to include them tomorrow, because it's very late now! (I guess there has to be some option for this in 'make xconfig'.)

Thank you for your hint! 

```

$ lsmod | sort
8139cp                 25088  0 
8139too                27520  0 
ac                      6404  0 
acpi_cpufreq           10696  1 
af_packet              24840  6 
agpgart                35272  3 drm,intel_agp
ata_generic             8708  0 
ata_piix               17668  3 
battery                11268  0 
button                  9232  0 
capability              6024  0 
cdrom                  37792  1 sr_mod
commoncap               8576  1 capability
container               5632  0 
cpufreq_conservative     8328  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2944  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
dock                   10784  0 
drm                    83988  2 i915
ehci_hcd               36364  0 
evdev                  11392  6 
ext3                  134024  2 
fan                     6020  0 
freq_table              6048  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
fuse                   46996  1 
i915                   25984  1 
ieee1394               96440  2 sbp2,ohci1394
intel_agp              25748  1 
ipv6                  272612  10 
iTCO_vendor_support     5124  1 iTCO_wdt
iTCO_wdt               12068  0 
jbd                    59688  1 ext3
joydev                 11584  0 
libata                125168  2 ata_piix,ata_generic
lp                     12708  0 
mbcache                 9860  1 ext3
mii                     6784  2 8139too,8139cp
Module                  Size  Used by
ohci1394               36656  0 
parport                37704  3 ppdev,parport_pc,lp
parport_pc             37540  0 
pci_hotplug            32960  1 shpchp
pcspkr                  4352  0 
ppdev                  10500  0 
processor              32328  2 acpi_cpufreq,thermal
psmouse                40208  0 
rt73                  214784  0 
sbp2                   24328  0 
sbs                    19720  0 
scsi_mod              147212  5 sbp2,sg,sr_mod,sd_mod,libata
sd_mod                 30464  4 
serio_raw               8324  0 
sg                     37020  0 
shpchp                 34836  0 
sr_mod                 17956  0 
thermal                14600  0 
uhci_hcd               26768  0 
usbcore               138504  4 rt73,ehci_hcd,uhci_hcd
video                  18188  0 

```

---

### Post by Nepherte on 2008-02-16
You may want to compile the alsa drivers manually: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by jjalocha on 2008-02-16
I just re-compiled the kernel. I don't know why, but Intel HDA was disabled, so I had to activate it.

```

Device Drivers
> Sound
> Advanced Linux Sound Architecture
> PCI devices
> Intel HD Audio

```

Sound works now, but I might want to compile the Alsa drivers as you suggested, since some things are working less than optimal (automatic jack headphone detection doesn't work, for example).

Thank you very much for your help!

---

