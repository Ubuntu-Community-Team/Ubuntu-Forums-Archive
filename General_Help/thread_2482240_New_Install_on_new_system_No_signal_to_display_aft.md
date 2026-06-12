---
title: "New Install on new system: No signal to display after waking from suspend"
date: 2022-12-25
forum: General Help
---

### Post by stevo92 on 2022-12-25
I have recently installed Ubuntu 22.04.1 LTS (Jammy Jellyfish) on a new system that I built. MOBO is Gigabyte X670 Aorus Elite AX. Cpu is AMD Ryzen 9 7950X. Memory is Samsung 970 EVO Plus 2TB SSD. RAM is G.SKILL Trident Z5 Series 64GB (2 x 32GB) 288-Pin PC RAM DDR5 6000 (PC5 48000). I am running Integrated Graphics (No Gpu Installed yet). The Kernel version is 5.15.0-56-generic x86_64.

When I first tried to install Ubuntu it kept throwing errors saying (I am paraphrasing here) that the compressed data on the bootable usb was corrupt. I kept redownloading the .iso file and verified the checksums and it kept throwing errors. Sometimes It would boot and I would make it all the way to the part where I setup my user account, only to have the installer crash, and I would try again. Finally, after flashing my BIOS with the latest firmware, I was able to get the Ubuntu OS installed (with the exact same USB I was using before when it kept complaining about corrupted data, so the USB was absolutely fine LOL). So, my system is running great now except for a few small problems...

1) When I boot up, I get these messages:
[LIST]
[*]ACPI BIOS Error (bug): Failure creating named object [\_SB.PCIO.GPP7._PRW], AE_ALREADY_EXISTS (20210730/dswload2-326)
[*]ACPI Error: AE_ALREADY_EXISTS , During name lookup/catalog (20210730/psobject-220)
[*]ACPI BIOS Error (bug): Failure creating named object [\_SB.PCIO.GPP2._PRW], AE_ALREADY_EXISTS (20210730/dswload2-326)
[*]ACPI Error: AE_ALREADY_EXISTS , During name lookup/catalog (20210730/psobject-220)
[*]ACPI BIOS Error (bug): Failure creating named object [\_GPE._L08], AE_ALREADY_EXISTS (20210730/dswload2-326)
[*]ACPI Error: AE_ALREADY_EXISTS , During name lookup/catalog (20210730/psobject-220)
[*]hub 10-0:1.0: config failed, hubdoesn't have any ports! (err -19)
[*]/dev/nvmeOn1p2: clean, 234146/122068992 files, 11210370/488247296 blocks
[*]mt7921e 0000:0e:00.0: ASIC revision: 79220010
[*]mt7921e 0000:0e:00.0: Firmware init done
[/LIST]
2) When I try to suspend my system, everything seems to go OK until I try to wake it by pressing a key on the keyboard.


[LIST]
[*]The fans begin spinning back up in the case, so that tells me that the machine recognizes my input and is trying to wake back up.
[*]The monitor, however, shows "No Signal". Now, this is a TV connected over HDMI that I am using because I do not have a monitor yet, but I have one ordered and it is on the way. (NOTE: It may actually be the TV or HDMI because I recently learned that when I turn my computer on, the monitor must be turned on first or I will get a similar "No Signal" message that will not go away unless I power cycle the PC, power cycling the TV does nothing.) I don't really understand how the HDMI protocol works, but it seems like the issue is more related to the PC not sending signal down the wire because it does not sense that a device is connected, rather than an issue with the TV itself.
[*]I ran this command $ journalctl -b -1 | tee >(gzip --stdout > journalctl_$USER.gz)      which supposedly gives me a log file containing everything that happened from the initial boot to the point where I have to do a hard reset on the computer after trying to suspend the system and the screen never comes back on. I got this far by researching on the internet and I got that command off a post on reddit over at [https://forums.linuxmint.com/viewtopic.php?t=346628](https://forums.linuxmint.com/viewtopic.php?t=346628)
[*]I have attached the gzip file containing the system log info to this post.
[/LIST]
This is as far as Iv'e gotten. I cannot understand the info in the gzip file, but I'm hoping someone on here can help me understand it and fix the issue. I believe that the boot errors in problem 1 are fairly common and harmless, but I would also like someone to explain to me what they mean and if there is any way that I can get rid of them. Thanks guys.

---

### Post by Tadaen_Sylvermane on 2022-12-25
I see a bunch of errors like that on Debian boot. Thus far it doesn't seem to have caused any problems. Without knowing exactly when Jammy cloned the testing / unstable Debian I can't say for certain but I recently solved my screen not waking up by disabling Wayland altogether. May be the same issue.

/etc/gdm3/daemon.conf

```
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
# Uncomment the line below to force the login screen to use Xorg
WaylandEnable=false
```

All I did was uncomment that and restart gdm. I've been able to wake it first try every try the last couple days without a hitch.

Whether or not it belongs in stable Debian or Ubuntu I don't know but that problem alone tells me Wayland isn't ready.

---

### Post by stevo92 on 2022-12-26
I tried uncommenting that line, but unfortunately it did not solve the problem. However, I noticed today when I went to turn on my computer that if I do not turn my TV on first before turning on my computer, it also leads to the screen receiving no input. This is very weird. The only thing I can think of is that HDMI devices can sense if they are connected to another device and since the monitor has no power, maybe the computer thinks that their is nothing plugged into the HDMI port and decides not to send a signal out that port. I did know of this behavior when I wrote the initial post, so I will try to edit the post accordingly. My theory still fails to explain why the TV never receives a signal from the PC once it wakes back up because the TV is definitely on the entire time. I have also tried turning the TV off and on again, but the only thing that seems to work is turning the PC off and on again, and that defeats the purpose of suspending the PC because none of your work is saved. I'm hoping that when I get my actual computer monitor it will just work.

---

