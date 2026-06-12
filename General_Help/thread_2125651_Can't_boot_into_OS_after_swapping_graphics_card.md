---
title: "Can't boot into OS after swapping graphics card"
date: 2013-03-14
forum: General Help
---

### Post by sbcontt on 2013-03-14
Hello.

Here is initctl list:

```

avahi-daemon start/running, process 946
cgroup-lite start/running
mountall-net stop/waiting
nmbd start/running, process 1463
passwd stop/waiting
qemu-kvm start/running
rc stop/waiting
rsyslog start/running, process 573
screen-cleanup stop/waiting
tty4 start/running, process 1582
udev start/running, process 563
upstart-udev-bridge start/running, process 535
ureadahead-other stop/waiting
apport start/running
console-setup stop/waiting
hwclock-save stop/waiting
irqbalance start/running, process 1710
plymouth-log stop/waiting
smbd start/running, process 1065
tty5 start/running, process 1589
failsafe stop/waiting
hybrid-gfx stop/waiting
atd start/running, process 1656
dbus start/running, process 579
ecryptfs-utils-restore stop/waiting
mounted-var stop/waiting
plymouth stop/waiting
resolvconf start/running
ssh start/running, process 1416
udev-fallback-graphics stop/waiting
control-alt-delete stop/waiting
hwclock stop/waiting
mounted-proc stop/waiting
alsa-store stop/waiting
module-init-tools stop/waiting
setvtrgb stop/waiting
shutdown stop/waiting
alsa-restore stop/waiting
cron start/running, process 1655
mountall start/running, process 379
mounted-debugfs stop/waiting
binfmt-support stop/waiting
console stop/waiting
mounted-run stop/waiting
acpid start/running, process 1648
bluetooth start/running, process 910
libvirt-bin start/running, process 1759
lxdm stop/waiting
plymouth-stop stop/waiting
rcS stop/waiting
ufw start/running
wait-for-state stop/waiting
flush-early-job-log stop/waiting
friendly-recovery stop/waiting
rc-sysinit stop/waiting
cups start/running, process 1049
upstart-socket-bridge start/running, process 1076
anacron start/running, process 1647
tty2 start/running, process 1617
udevtrigger stop/waiting
container-detect stop/waiting
mounted-dev stop/waiting
teamviewerd stop/waiting
tty3 start/running, process 1618
udev-finish stop/waiting
cryptdisks-udev stop/waiting
dovecot start/running, process 1646
hostname stop/waiting
mountall-reboot stop/waiting
mysql start/running, process 1692
mountall-shell stop/waiting
mounted-tmp stop/waiting
network-interface (virbr0) start/running
network-interface (lo) start/running
network-interface (eth0) start/running
network-interface (wlan0) start/running
plymouth-splash stop/waiting
plymouth-upstart-bridge stop/waiting
tty1 start/running, process 2608
udevmonitor stop/waiting
cryptdisks-enable stop/waiting
dmesg stop/waiting
network-interface-security (network-interface/eth0) start/running
network-interface-security (network-interface/wlan0) start/running
network-interface-security (network-interface/lo) start/running
network-interface-security (network-interface/virbr0) start/running
network-interface-security (networking) start/running
networking stop/waiting
procps stop/waiting
tty6 start/running, process 1622
ecryptfs-utils-save stop/waiting
network-interface-container stop/waiting
ureadahead stop/pre-stop, process 376
pre-stop process 2606

```

Here is dmesg:

pastebin.ca/2332332

Please help.

---

### Post by matt_symes on 2013-03-16
Hi

If you cannot boot into your OS, how have you got the list of services running using initctl ?

Much more information is required to even attempt a diagnosis.

What exactly happens when you boot ? Please give as full a description as possible.

You dmesg trace is showing a kernel panic due to a buggy BIOS but that does not seem to be stopping the boot process but it could be the cause of your problems.

Much more information please.

Kind regards

---

### Post by sbcontt on 2013-03-16
I am able to run initctl and dmesg thanks to this: [http://blog.tridgell.net/?p=57](http://blog.tridgell.net/?p=57)
I had temporarily replaced a GTX 560TI with a GTX 550TI. Not sure if that is the reason, but the OS is not booting ever since. The OS has no Desktop environment, so I do not use driver for X; I only have Nouveaufb driver. Currently boot halts at "Attempting to load BIOS image from PRAMIN...."
Please tell me what info is necessary and I will try to provide.

---

### Post by matt_symes on 2013-03-16
Hi

> **sbcontt said:**
>  Currently boot halts at "Attempting to load BIOS image from PRAMIN...."

```

[LIST=1]
[*][    0.000000] Your BIOS is broken; DMAR reported at address fed90000 returns all ones! 
[*][    0.000000] BIOS vendor: American Megatrends Inc.; Ver: 0406   ; Product Version: System Version 
[*][    0.000000] Modules linked in: 
[*][    0.000000] Pid: 0, comm: swapper Not tainted 3.2.0-38-generic #61-Ubuntu 
[*][    0.000000] Call Trace: 
[*][    0.000000]  [<ffffffff81067e3f>] warn_slowpath_common+0x7f/0xc0 
[*][    0.000000]  [<ffffffff81067edf>] warn_slowpath_fmt_taint+0x3f/0x50 
[*][    0.000000]  [<ffffffff81d121b2>] ? __early_set_fixmap+0x96/0x9d 
[*][    0.000000]  [<ffffffff8151fcff>] warn_invalid_dmar+0x8f/0xa0 
[*][    0.000000]  [<ffffffff81d1261b>] ? early_iounmap+0xe4/0x12e 
[*][    0.000000]  [<ffffffff81d39e41>] check_zero_address+0xc8/0xf7 
[*][    0.000000]  [<ffffffff8166a8cc>] ? bad_to_user+0x7f6/0x7f6 
[*][    0.000000]  [<ffffffff81d39e87>] detect_intel_iommu+0x17/0xb8 
[*][    0.000000]  [<ffffffff81d04acb>] pci_iommu_alloc+0x44/0x6f 
[*][    0.000000]  [<ffffffff81d11f75>] mem_init+0x19/0xec 
[*][    0.000000]  [<ffffffff81cfca2d>] start_kernel+0x1da/0x3bd 
[*][    0.000000]  [<ffffffff81cfc388>] x86_64_start_reservations+0x132/0x136 
[*][    0.000000]  [<ffffffff81cfc140>] ? early_idt_handlers+0x140/0x140 
[*][    0.000000]  [<ffffffff81cfc459>] x86_64_start_kernel+0xcd/0xdc 
[*][    0.000000] ---[ end trace 372d3a9968dbaa88 ]--- 
[/LIST]

```  

[LIST=1] 
[/LIST]

That is where you are getting the kernel panic in dmesg. When did this start happening ? Only after the new card was installed ? After a kernel update ?

In the first instance, try booting an older kernel. Does it still crash ?

Boot into a LiveCD/USB. Does that boot ?

After that, reset the BIOS. 

That may be done with jumpers or from the BIOS itsels depending or you machine. You can also try to remove the CMOS battery to clear the BIOS. Does that fix it ?

Is there a BIOS update for your machine. Don't install yet, just check.

Kind regards

---

### Post by grahammechanical on 2013-03-16
Have you given any thought to the possibility that the video adapter is faulty? From this [http://nouveau.freedesktop.org/wiki/HwIntroduction](http://nouveau.freedesktop.org/wiki/HwIntroduction) I get this > [COLOR=#000000][FONT=Times New Roman]VBIOS copies its own image to first 64kiB of PRAMIN when it boots[/FONT][/COLOR] and from this [http://en.wikipedia.org/wiki/Video_BIOS](http://en.wikipedia.org/wiki/Video_BIOS) I get this > [COLOR=#000000][FONT=sans-serif]The video BIOS interfaces software to the video [/FONT][/COLOR][chipset]("http://en.wikipedia.org/wiki/Chipset")[COLOR=#000000][FONT=sans-serif] in the same way that the system BIOS does for the system chipset.[/FONT][/COLOR]

I doubt very much if the boot process is getting further than trying to run the settings in the Video BIOS. This > [COLOR=#000000]"Attempting to load BIOS image from PRAMIN...."[/COLOR] is the Video BIOS (VBIOS). Think - faulty graphic adapter.

Regards.

---

### Post by matt_symes on 2013-03-16
Hi

>  					Have you given any thought to the possibility that the video adapter is faulty?




This is good research and sounds like the culprit. 

I misread an earlier post and thought that both cards were causing problems.

If it's not a hardware failure, it may be possible to flash the video cards BIOS but this is it not something i have ever tried. So this is only a vague suggestion.

Kind regards

---

### Post by sbcontt on 2013-03-18
Using old kernel does not work. The owner of the 550 card also runs Ubuntu (10.10) so the card should work with a LiveCD or a new installation.
I'll try resetting the BIOS.

Thanks for the research people. I know that it is almost guranteed that a new installation of ubuntu will solve the issue, but this is not Windows and I want to learn. Sadly, for whatever reason my search with the "PRAMIN" error had been futile.

---

### Post by cdnwolverine on 2013-03-18
I have a Nvidia GeForce 550Ti and when I was installing 12.04 it would hang on boot unless I had **nomodeset** **noquiet nosplash** entered in the startup line. After the initial startup, I would let it install the official Nvidia driver. After which it was fine.

I haven't had the same issues with 12.10 however; 12.10 installs just fine with the 550Ti installed and it worked in version 11.xx just fine as well -- just something funny with 12.04 I think.

---

### Post by FabulousCabbage on 2013-03-18
I could be completely wrong here, but could it be that the operating system is running the drivers for the old card, and obviously not working with the new card?
I had this problem when I installed the wrong drivers and I was just loading into ubuntu without a desktop environment, and the startx command brought back errors with xrandr and things like that.

---

### Post by sbcontt on 2013-03-20
I tried resetting the BIOS, and now the "....PRAMIN..." message is gone, but the problem remains. Boot stops at "fbcon: nouveaufb(fb0) is primary device "
However, safe mode boots.
cdnwolverine, nomodset noquiet nosplash won't help me; because I do not have X11 startup. So those three are given anyway. Here is something that worked: acpi=off
But of course things can not go on like this. It sucks that nouveau is tied to kernel and I must recompile the kernel to reconfigure it (as far as I know, of course).

Maybe FaboulasCabbage is right; it is time to move to 12.10. I have /home in NAS, and just backed up /etc. But restoring all scripts in /etc one-by-one is slow. Can /etc be migrated to a new installation as a whole?

---

