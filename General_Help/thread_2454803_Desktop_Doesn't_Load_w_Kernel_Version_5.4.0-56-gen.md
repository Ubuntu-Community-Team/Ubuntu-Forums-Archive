---
title: "Desktop Doesn't Load w/ Kernel Version 5.4.0-56-generic"
date: 2020-12-06
forum: General Help
---

### Post by windows7ge on 2020-12-06
Hello, about a week ago I started up my Ubuntu 20.04.1 LTS Desktop and it would perform the following start-up sequence:


[LIST=1]
[*]Ubuntu logo (it would sit on this longer than usual)
[*]Spinning icon w/ Ubuntu logo
[*]Suddenly display a list of all the loaded components (too quickly for me to read but looked all green as far as I can tell)
[*]Then a black screen followed by a blinking cursor
[*]The screen would then go black to blinking cursor, black, blinking cursor, etc. (about 5 times)
[*]Then settle on the black screen with blinking cursor and not change there-after.
[/LIST]

I tried escaping into Terminal (Ctrl+Shift+F2?) but it doesn't respond. Ctrl+Alt+Del does result in a restart though. I have software that runs on startup that I can monitor over the Internet and it tells me the OS is loading properly as the software is working it's just the desktop environment isn't loading. During troubleshooting I clicked ESC during start-up to escape into the GRUB2 menu and selected the advanced start-up options at which time I tried booting into Ubuntu with the previous kernel listed (5.4.0-54-generic) and for the past few days it has been working perfectly. The desktop environment is loading once again perfectly fine.

So I don't know if I have a hardware incompatibility with Kernel 5.4.0-56-generic, if it's a bug, if it's conflicting with another piece of software on the system, or what.

Specs:
AMD TR 1950X
4x8GB DDR4 2400MHz from G.Skill
ASUS PRIME X399-A motherboard
2x Sapphire Tri-X R9-290X's
Corsair AX1200i
Broadcom BCM57810
Samsung 960PRO 1TB NVMe SSD

My own guesses: I installed the AMD GPU driver from the AMD website so I could have OpenCL support for compute applications. Maybe it has something to do with that?

---

### Post by crip720 on 2020-12-06
Do not know if it works the same for AMD, but if secure boot is enabled, then nivida drivers can have problems being installed/working.

---

### Post by CelticWarrior on 2020-12-06
Yes, it's the same problem at least for the proprietary AMD drivers the OP installed.
And, in the case of this hardware, newer kernel versions are also recommended.

---

### Post by windows7ge on 2020-12-06
> **crip720 said:**
> Do not know if it works the same for AMD, but if secure boot is enabled, then nivida drivers can have problems being installed/working.

> **CelticWarrior said:**
> Yes, it's the same problem at least for the proprietary AMD drivers the OP installed.
And, in the case of this hardware, newer kernel versions are also recommended.

So both of you believe the issue is likely the proprietary AMD driver needs updating to work with the newer kernel?

Would you happen to know if I can just install over the old driver or if I have to figure out how to do a proper un-installation of it? (I think there's an uninstall script somewhere...)

---

### Post by crip720 on 2020-12-06
Depends if you have secure boot enabled, if not then a different problem.  I just went with simple fix first.  If secure boot enabled in bios, try with it disabled first.  CelticWarrior is probably thinking of using the 5.8 kernel, but I will let him explain better.

---

### Post by CelticWarrior on 2020-12-06
> **windows7ge said:**
> So both of you believe the issue is likely the proprietary AMD driver needs updating to work with the newer kernel?

No, quite the misunderstanding there.
I said newer kernel versions are usually recommended for better support of your AMD hardware. It has nothing to do with the proprietary AMD graphics drivers.

---

### Post by windows7ge on 2020-12-06
> **crip720 said:**
> Depends if you have secure boot enabled, if not then a different problem.  I just went with simple fix first.  If secure boot enabled in bios, try with it disabled first.  CelticWarrior is probably thinking of using the 5.8 kernel, but I will let him explain better.

I tried disabling secure boot and it made no difference.

> **CelticWarrior said:**
> No, quite the misunderstanding there.
I said newer kernel versions are usually recommended for better support of your AMD hardware. It has nothing to do with the proprietary AMD graphics drivers.

Do you have a particular version in mind? 5.8 as crip720 mentioned? I hope it should be possible to install one with the likes of Ukuu without it or the system deleting the kernel I know still works.

If the information is worth anything I have plans to step up to the RX 6800XT. I've been told it plays very friendly with VFIO.

---

### Post by CelticWarrior on 2020-12-06
Yes, 5.8 or newer.

---

### Post by windows7ge on 2020-12-06
> **CelticWarrior said:**
> Yes, 5.8 or newer.

Alright.

Apparently Ukuu is no longer free...I know I used a CLI kernel updater a long while ago. If I can remember what it was called...

---

### Post by Impavidus on 2020-12-07
If you install linux-generic-hwe-20.04-edge on Ubuntu 20.04, you'll get the 5.8 kernel from the official repositories.

---

### Post by windows7ge on 2020-12-07
> **Impavidus said:**
> If you install linux-generic-hwe-20.04-edge on Ubuntu 20.04, you'll get the 5.8 kernel from the official repositories.

Is this something I can download/install with apt or is there a different install process I have to go through?

---

### Post by deadflowr on 2020-12-07
> Is this something I can download/install with apt or is there a different install process I have to go through? 
You can install it through apt,
```
sudo apt install linux-generic-hwe-20.04-edge
```

You can read about Ubuntu's hardware enablement stacks here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop")
And information about the different stacks here:
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Implementation]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Implementation")

---

### Post by windows7ge on 2020-12-07
> **deadflowr said:**
> You can install it through apt,
```
sudo apt install linux-generic-hwe-20.04-edge
```

You can read about Ubuntu's hardware enablement stacks here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop)
And information about the different stacks here:
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Implementation](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Implementation)

When I get off work tonight I'll give it a shot and report back.

I remember briefly reading about HWE pertaining to the proprietary AMD driver. I will have to look over it again though as I've forgotten what it means.

In the meantime I was able to update the Kernel with uktools but the version it downloaded was hardly newer (if not older...) but the desktop does load again on it's own without my intervention at boot. Regardless I'll step up to 5.8 since I will need good AMD support for the newer hardware I plan on buying.

---

### Post by windows7ge on 2020-12-07
> **CelticWarrior said:**
> Yes, 5.8 or newer.

> **Impavidus said:**
> If you install linux-generic-hwe-20.04-edge on Ubuntu 20.04, you'll get the 5.8 kernel from the official repositories.

> **deadflowr said:**
> You can install it through apt,
```
sudo apt install linux-generic-hwe-20.04-edge
```

You can read about Ubuntu's hardware enablement stacks here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop)
And information about the different stacks here:
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Implementation](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Implementation)

Got 5.8.0-31-generic installed and it made no difference to the behavior. However using the older kernel 5.4.0-54-generic, or the one uktools downloaded 5.5.4-050504-generic the system boots with the desktop environment just fine.

So some issue on 5.4.0-56 that doesn't occur on 5.5.4-050504 but occurs again on 5.8.0-31.

I have no idea what's going on here.

---

### Post by windows7ge on 2020-12-09
Alright, I don't know if I just quoted you guys wrong or if all three of you gave up (hoping the former) but I came up with a work-around at least until I feel the time is right to just do a full system re-install.

So whatever is causing the desktop to not load on kernels 5.4.0-56 & 5.8.0-31 but work fine on 5.4.0-54 & 5.5.4-050504 is the only thing I'm worried about. No other functionally seems to be impacted at this time.

So what I've done is I've gone into /etc/default/grub and edited the default kernel with:
```

#GRUB_DEFAULT=0
GRUB_DEFAULT="gnulinux-advanced-ce7a9223-fe11-40c4-927c-d2f89654d6e2>gnulinux-5.5.4-050504-generic-advanced-ce7a9223-fe11-40c4-927c-d2f89654d6e2"


```
So now kernel 5.5.4-050504 starts at system boot and I hope subsequent system updates don't rewrite the GRUB file. If they don't then this fixes the problem until I feel like re-installing the OS or actually locate an error log somewhere that explains what's actually failing when the select kernels try to start the desktop service/program.

---

### Post by deadflowr on 2020-12-10
> Alright, I don't know if I just quoted you guys wrong or if all three of you gave up
I only posted to give the command of installing the upgrade kernel version and what it relates to in terms of hardware stacks.

> So now kernel 5.5.4-050504 starts at system boot and I hope subsequent system updates don't rewrite the GRUB file. 
The /etc/default/grub file will remain as is through updates.
If an update comes that want to overwrite that file you will be notified during the update if you want to keep the current file you have or replace it with the new version from the updated package.
Most all files related to the /etc directory are treated this way.

---

### Post by windows7ge on 2020-12-10
> **deadflowr said:**
> The /etc/default/grub file will remain as is through updates.
If an update comes that want to overwrite that file you will be notified during the update if you want to keep the current file you have or replace it with the new version from the updated package.
Most all files related to the /etc directory are treated this way.

Just in case I'm not paying attention and click through one of those updates without reading it I might make a grub.bak file.

---

