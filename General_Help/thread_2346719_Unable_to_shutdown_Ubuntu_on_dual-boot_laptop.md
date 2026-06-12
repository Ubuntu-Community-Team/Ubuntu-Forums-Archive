---
title: "Unable to shutdown Ubuntu on dual-boot laptop"
date: 2016-12-17
forum: General Help
---

### Post by distance7000 on 2016-12-17
Ok here we go. I've spent about a week on this already.
[B]
Summary of problem:[/B]
My Ubuntu-based installations get through shutting down the OS, but will not poweroff the laptop. It is the same for a reboot and I have to hold the power button to shut off (which actually causes a reboot, making this all the more irritating).
Additionally, I cannot suspend the OS properly. The screen goes black, but both the power button and power indicator light are still lit and the system becomes unresponsive until I hold the power button.

**The story so far:**
I have new Asus GL752 laptop with Windows 10 on it. I have no problems with lock, sleep, shutdown, or reboot on Windows 10. I started with a dual-boot installation of Ubuntu 16.04 on a separate partition. This had 3 main issues: fan-speed maxed, unable to adjust brightness, and would not shutdown. I was able to fix the first two with kernel parameters ([FONT=courier new]acpi_osi=! acpi_backlight=native[/FONT]), but the last remains. I tried several additional kernel parameters and bios settings (see section below), and then decided to try some additional distros to see if that made a difference and so far no luck. The system is running UEFI and I have made sure each OS is installed as such.

With 16.04, the systems gets through:
[ OK ] Reached target Unmount All Filesystems.
[ OK ] Stopped target Local File Systems (Pre).
[ OK ] Stopped Remount Root and Kernel File Systems.
[ OK ] Stopped Create Static Device Nodes in /dev.
[ OK ] Reached target Shutdown.

and then just sits there :(

[FONT=courier new][FONT=arial]With 14.04, the system gets through:[/FONT]
* Deactivating swap...
* Unmounting local filesystems...
* Will now halt

[FONT=arial]and then just sits there :([/FONT]
[/FONT]
On 16.04, I tried making small updates to the kernel (4.6.0, 4.6.7), but no luck there.

On 14.04, I tried updating to the latest kernel I could get my hands on (4.9)...
Using the 4.9 kernel ([FONT=courier new]4.9.0-040900-generic[/FONT]),  the fan speed issue has disappeared without any additional options,  which gave me hope...but sadly, no dice :( Stil doesn't shutdown  properly.

[B]OS Information:
[/B]Windows 10 on /dev/sda3
Ubuntu 16.04 on /dev/sda6[INDENT][FONT=courier new]NAME="Ubuntu"
[/FONT][/INDENT]
[INDENT][FONT=courier new]VERSION="16.04.1 LTS, (Xenial Xerus)"
Kernel=4.4.0-51-generic
Kernel=4.4.0-53-generic
Kernel=4.6.0-040600-generic
[/FONT][/INDENT]
[INDENT][FONT=courier new]Kernel=4.6.7-040607-generic[/FONT]
[/INDENT]

Elementary OS Loki on /dev/sda8[INDENT]NAME="elementary OS"
VERSION="0.4 Loki"
ID_LIKE=ubuntu
[/INDENT]
[INDENT]Kernel=4.4.0-38-generic
Kernel-4.4.0-53-generic
[/INDENT]

Ubuntu 14.04 on /dev/sda9[INDENT][FONT=courier new]NAME="Ubuntu"
[/FONT][/INDENT]
[INDENT][FONT=courier new]VERSION="14.04.5 LTS, Trusty Tahr"
Kernel=4.4.0-31-generic
Kernel=4.4.0-53-generic
Kernel=[FONT=courier new]4.9.0-040900-generic[/FONT][/FONT]
[/INDENT]


**Some things I have tried** (based on suggestions found around the internet):
[LIST]
[*]Disable Wake on LAN (no option in BIOS, but did this in Windows 10) 
[*]Disable Wake on Lid Open in BIOS 
[*]Disable Launch CSM in BIOS 
[*]Disable "Fast Boot" in both the BIOS and Windows 
[*]Updating to latest BIOS (214, was 213) 
[*]Turn off USB Legacy mode in BIOS 
[*]Updated all packages with apt, dpkg, and update-grub 
[*]sudo swapoff -a && systemctl poweroff 
[*]Use [FONT=courier new]sudo shutdown -h now[/FONT] or [FONT=courier new]sudo shutdown -P now[/FONT] or [FONT=courier new]sudo poweroff[/FONT] 
[*][FONT=courier new]alt + SysReq, R E I S U B (screen goes black, similar to suspend hang)[/FONT] 
[*][FONT=courier new]alt + SysReq, R E I S U O (interesting output, will try to post later)[/FONT] 
[*][FONT=courier new]ctrl + alt + F1 after the hang (this gets me a prompt, but does nothing after that)[/FONT] 
[*][FONT=courier new]acpi_osi=!, Linux, Windows[/FONT] 
[*][FONT=courier new]idle=nomwait[/FONT] 
[*][FONT=courier new]apm=power_off[/FONT] 
[*][FONT=courier new]reboot=acpi,bios (etc. etc. tried the entire list of options)[/FONT] 
[/LIST]
[FONT=courier new]
[FONT=arial]**The best lead I have:**[/FONT]
[/FONT]When trying to install both Elementary OS and Ubuntu 14.04, I found they would halt with a particular wifi issue ([FONT=courier new]iwlwifi [...] Unsupported splx structure[/FONT], [this link is where I found the fix]("http://askubuntu.com/questions/728631/ubuntu-15-10-live-wont-boot-nouveau-and-nvidia")), and I needed to set the kernel parameter [FONT=courier new]nomodeset[/FONT] to get it to boot to the installation. I have used [FONT=courier new]nomodeset[/FONT] to boot all 3 distros and they all shutdown/reboot properly with this setting, but suspend still doesn't work right. I could live with that...except the graphics are terrible with this setting (looks kind of like Windows in safe mode).
[B]
Why I'm here:[/B]
I've exhausted all of my usual resources and I'm frustrated with guessing at random. I would appreciate a more systematic approach like "let's eliminate a, b, c, and it must be d" or "let's get some additional log output and see what errors there are", but I'm willing to try any ideas you guys can come up with. Thanks in advance.

---

### Post by mörgæs on 2016-12-18
Welcome to the fora. You have done a good effort already, so I can only suggest a minor low-tech attempt: Have you tried pushing Return or Escape at the screen that hangs?

---

### Post by distance7000 on 2016-12-18
Thanks! In good faith, I've tried this just now. Pressing Escape or Enter doesn't appear to do anything at that stage.

---

### Post by distance7000 on 2016-12-18
Interesting...your post made me stumble into something with potential...I tried Esc/Enter and nothing, so then I thought "I'll try with the tty prompt again." The key presses still do nothing, but I got [this error about irq]("http://stackoverflow.com/questions/13861282/understanding-kernel-message-nobody-cared-try-booting-with-the-irqpoll-optio"). Following that suggestion, when I add [FONT=courier new]irqpoll[/FONT] to the kernel parameters, 16.04 has shutdown correctly on 4 out of 5 attempts.

What does irq do? Seemingly it has something to do with my issue.

---

### Post by distance7000 on 2017-01-08
I have finally found a stable fix for my Asus GL752VW laptop not shutting down properly, so I'm posting it here in the hopes that it will help someone else in the future.
[B]
short version:
[/B]
I am using kernel 4.9.0 with these parameters (added to the "linux" line after "ro"):
```
acpi_osi=! acpi_backlight=native irqpoll nouveau.modeset=0 idle=nomwait
```

**long version:**

After my previous posts, I decided to try the [FONT=courier new]irqpoll[/FONT] kernel parameter together with [FONT=courier new]kernel 4.9.0[/FONT] on Ubuntu 16.04. This idea worked very well and I got 100% shutdown/reboots with 16/16 tries. I noticed just before the shutdown these messages would display:

```

[ OK ] Reached target Shutdown.
nouveau 0000:01:00.0: priv: HUB0: 6013d4 0000573f (19408200)
nouveau 0000:01:00.0: priv: HUB0: 6013d4 0000573f (19408200)
reboot: Restarting system

```

I believe the above is telling me [the interrupt handlers]("http://stackoverflow.com/questions/13861282/understanding-kernel-message-nobody-cared-try-booting-with-the-irqpoll-optio") that failed and/or were subsequently polled. The *nouveau* part is important, as I will explain below...

At the same time, I finally came across [this Asus forums thread with detailed information]("https://rog.asus.com/forum/showthread.php?81702-Linux-installation-in-ASUS-ROG-GL552VW-DH71&p=564158&viewfull=1#post564158") on what the kernel parameters are doing (which I will copy here in case of link-rot), so I combined that to get my ultimate solution.

> 
Kernels below 4.3 (pretty much any distro at the end of December): Add  "nouveau.modeset=0 tpm_tis.interrupts=0 acpi_osi=! acpi_backlight=native  i915.preliminary_hw_support=1 idle=nomwait"

The Nouveau command disables the NVidia card, which you need to do until  you get proper drivers installed (use something like Bumblebee).
The ACPI commands make your keyboard hotkeys work properly
The i915 command tells the older kernel to use the "beta" Skylake support, which you will certainly want.
The idle command is needed to make the new Skylake chipset speed up and  down properly without locking up. I was seeing occasional lockups  without the idle setting.
[...]
For 4.3 and above kernels (which I have custom compiled from source at  this point but should be rolling out on some distros soon) you can drop  the i915.preliminary_hw_support and tpm_tis.interrupts. You don't need  those on the latest kernel as far as I can tell. 

Don't use things like "nolapic" and other stuff you read on the internet  because all that does is drop you down to one core and limit your  hardware significantly. Might as well not have the new computer if you  use those things.


As you can see, [nouveau]("https://nouveau.freedesktop.org/wiki/") is related to NVidia cards in the linux kernel. I do not have the NVidia drivers installed, so I want to disable it (at least for now). And I'm using Kernel 4.9, which is newer than 4.3, so I just needed to add the following:
[FONT=courier new]nouveau.modeset=0[/FONT]. I also added [FONT=courier new]idle=nomwait[/FONT] trying to fix some of the graphical tearing I saw using Intel graphics. So in total, I now have my parameters as:

```
acpi_osi=! acpi_backlight=native irqpoll nouveau.modeset=0 idle=nomwait
```

With this, I can shutdown, reboot, and even suspend without any issues (and the tearing is gone!), so I'm pretty psyched about that :grin: Also, I no longer see the [FONT=courier new]nouveau HUB0[/FONT] messages at shutdown, so I think I can remove [FONT=courier new]irqpoll[/FONT], but I have not tried it like that yet.

So, I am *speculating* that the root cause can be summarized as: At shutdown, the system is waiting for a signal from the Nvidia graphics drivers, but they are not installed, and this is causing the shutdown to hang.

---

