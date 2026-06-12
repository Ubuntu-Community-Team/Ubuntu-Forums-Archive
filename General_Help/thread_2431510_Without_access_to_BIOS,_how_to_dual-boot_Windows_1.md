---
title: "Without access to BIOS, how to dual-boot Windows 10 and Ubuntu?"
date: 2019-11-17
forum: General Help
---

### Post by armadal on 2019-11-17
I'm currently renting a root server from Hetzner for hosting game servers, but unfortunately, some of them run horribly under WINE, others running horribly on Windows. So I need to dual-boot my existing Windows 10 install, with Ubuntu (ideally Lubuntu with SSH daemon, since it's the most performant distro with a GUI). There is a problem; there is no way to access the BIOS outside of renting a KVM console at a specific scheduled time.

Apparently, Wubi can be used to install Ubuntu without access to the BIOS. Is that true? If not, is there an alternative method?

As for selecting which OS I want to use, I know that the GRUB bootloader can be issued a command to boot into a specific OS. But since I have an existing Windows 10 install, I assume that uses the Windows bootloader. Is there a way to select which OS to reboot into? MSConfig should offer that functionality, but cannot find anything on it supporting non-Windows OS installs.

---

### Post by Frogs Hair on 2019-11-17
Wubi is no longer officially supported and exists as 3rd party project available on Github. Any support for that type of installation would have to come from the developer. It is uefi so that indicates some interaction with the bios. I have no idea if Windows 10 is supported !

---

### Post by yancek on 2019-11-17
Not knowing what your setup is with the company you are renting the server from, it's really not possible to give a specific answer.  We can answer the question about WUBI which was done in the post above.  THe last Ubuntu that worked on was released 5 years ago and I think 12.04 was the last official support.

The standard method on a compter to install both on the same drive would be to resize (shrink) the largest windows partitions to create unallocated space on which to install Ubuntu.  Windows 10 is almost certainly UEFI so Ubuntu would need to be also.  THe Ubuntu Grub would then be used to chainload the windows OSs. To my knowledge, windows UEFI will only boot recent windows releases and no other OS.  You might be best off contacting the company you lease server space on to find out what your options are.

---

### Post by armadal on 2019-11-18
> **yancek said:**
> Not knowing what your setup is with the company you are renting the server from, it's really not possible to give a specific answer.  We can answer the question about WUBI which was done in the post above.  THe last Ubuntu that worked on was released 5 years ago and I think 12.04 was the last official support.

The standard method on a compter to install both on the same drive would be to resize (shrink) the largest windows partitions to create unallocated space on which to install Ubuntu.  Windows 10 is almost certainly UEFI so Ubuntu would need to be also.  THe Ubuntu Grub would then be used to chainload the windows OSs. To my knowledge, windows UEFI will only boot recent windows releases and no other OS.  You might be best off contacting the company you lease server space on to find out what your options are.

My bad. It's a dedicated root server from Hetzner, which I have almost full control over. I sent an email to Hetzner, with them saying that they don't provide any support on software installs. Wubieufi states that it works with the default Windows boot loader, but it only supports Ubuntu 19.04, and has prompts during installation so it's a no-go, unfortunately.

I've learned that they do offer a remote KVM console for accessing the BIOS, but has to be ordered in advance, and can be used for 3 hours at the most. I can give that a try, but it's not ideal; learning how to do this without having to order a console every time I need to reinstall an OS.

---

### Post by TheFu on 2019-11-18
Why not use virtual machines?

---

### Post by armadal on 2019-11-18
A few reasons. Primarily, I want the absolute best performance for the game servers, and system calls are horrendously slow in VMs, with Conan Exiles' dedicated server in particular making tons of system calls. There's also cost, as the free VM's I've tried are exceedingly slow, and I'm not going to pay through the nose for mediocre performance. I'll also be repeatedly compiling the source code for AzerothCore, which compounds the need for performance.

As an update, I got a hold of the KVM console to access the BIOS, but getting Ubuntu to install was a failure. I got as far as partitioning the SSD, having created a 230GB partition for Ubuntu, a 5GB partition for the swap file, and a 1GB partition for the boot record thing. The partitions were placed after the pre-existing Windows partitions. Partitioning succeeded, but the next step failed with the error: "**Installation step failed: Installing the system**". Google is fruitless, and didn't yield any answers.

This was with the Ubuntu 19.04 minimal ISO, with the file name "**ubuntu-19.04-server-amd64.iso**".

Here's a screenshot of the partitions prior to running the Ubuntu installer: [https://i.imgur.com/oAxlFb6.png](https://i.imgur.com/oAxlFb6.png)

The error is not exactly giving me much to work with, so I can't figure out how to solve it.

---

### Post by TheFu on 2019-11-18
Linux KVM/qemu is faster than other hvm hypervisors.  For non-GPU related workloads, 95% of native is achievable.  It is extremely stable.  I've used esxi, esx, 6 VMware hypervisors, and Xen.  KVM/qemu is faster and more forgiving on hardware selection since it supports any Linux hardware with VT-x (or whatever AMD calls theirs).

If you can use Linux Containers for the game servers, then native performance is possible and usually a 10x density ratio compared to HVM hypervisors.

19.04 support ends in January.  It would be foolish to use this as a base for any install today, unless it was a test in a lab.  Production needs to use 18.04.

If you are tied to Windows on the hostOS, I cannot help. Sorry.  We run Windows inside VMs and don't have any Win10.

BTW, we need to be clear.  I know you are using KVM differently than I am.  I use both a KVM switch and KVM virtual machines. ;)

---

### Post by armadal on 2019-11-18
See, I need that 5% more performance. The GPU is just used as a display device for the server, but the game servers are not exactly optimized for multithreaded workloads so I need every last drop of performance. I've looked at Docker, but it requires you to have the source code and build the container for yourself. That's not doable since the games' server software is closed source.

Hetzner doesn't provide a 19.10 ISO, but I figured I'd just update the Ubuntu version via the command line before I install any software on it. Is that ill-advised for some reason?

About KVM, that's just the name of the remote viewer that Hezner attaches to your server upon request: [https://wiki.hetzner.de/index.php/KVM-Console/en](https://wiki.hetzner.de/index.php/KVM-Console/en)

My current issue still stands unfortunately, as I can't for the life of me find a solution to that error.

---

### Post by oldfred on 2019-11-18
Were you installing in UEFI boot mode? How you boot install media UEFI or BIOS is then how it installs.
Since Windows is UEFI, Ubuntu needs to be UEFI.

And if you try to install in BIOS mode, it has to have a bios_grub partition for the BIOS boot version of grub, otherwise install fails. Usually if that is issue, it will say it could not install grub. But those that have reported that were all desktop installs, not server type installs.
 
With UEFI you already have the ESP - efi system partition which grub will share with Windows.

---

### Post by armadal on 2019-11-18
Unfortunately, the BIOS screen only shows for an instant, before booting the mounted ISO. The couple times I managed to access the boot device selection screen, it doesn't say whether the virtual CD drive uses UEFI or not.

---

### Post by TheFu on 2019-11-18
For a remote server, you really need a RIBLO card in the server, on a completely different subnet.  About once a year, MSFT will update their boot sequence and break booting of any other OS.  Without the RIBLO card, the system will be down until they reconnect the console switch and you can fix it remotely.

With a RIBLO, you can do everything except physically connect a USB flash drive or drop optical media into the drive slot.

There are a few different names for RIBLO and there have been huge, huge, security issues over the decades with each of the different implementations.  [https://www.itworld.com/article/2708437/ipmi--the-most-dangerous-protocol-you-ve-never-heard-of.html](https://www.itworld.com/article/2708437/ipmi--the-most-dangerous-protocol-you-ve-never-heard-of.html)
I used to work at a very large enterprise with over 100,000 servers. We put RIBLOs into every one of our Intel servers because the cost in downtime and hassle even with onsite people 24/7/365 was more expensive than buying those cards.  The card is specific to the server - support is needed on both sides.

I don't know anything about the gaming setup, but almost always, the OS and applications aren't tuned very well.  I've seen 32-way servers replaced with 64-way systems (5 systems in total) because the official vender didn't think to add a few DB indexes.  Our DBAs looked over everything, added about 10 indexes and utilization dropped to under 30% on the old systems.  Unfortunately, the company had already spent many, many, millions to upgrade those servers.  Look at tuning if you can't just do a fork lift fix.

---

### Post by armadal on 2019-12-01
Sorry for the late reply.

Luckily, I've installed Windows 10 LTSC, so only updates that I manually select, and manually choose to install, will ever be installed. Bonus, Windows 10 will only look for updates when I do so manually. So that's not an issue.

But what is an issue, is that I still can't figure out how to get Ubuntu Minimal to install to the created partitions. Throws the same error, and there's nothing for me to go off of.

Is there a way to have the Ubuntu Minimal ISO, which is written to a USB stick, output a log file that actually says what caused the failure?

---

### Post by oldfred on 2019-12-01
I thought the minimal did not have UEFI.
Those that need UEFI can install server, but not install any of the server apps with 

       Used by Server install to choose what you want
sudo apt install tasksel
sudo tasksel
sudo apt install ubuntu-server
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel) 
    
       Minimal will not install in UEFI mode, but server will
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

