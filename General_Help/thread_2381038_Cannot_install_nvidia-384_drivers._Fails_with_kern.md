---
title: "Cannot install nvidia-384 drivers. Fails with kernel oops (17.10)"
date: 2017-12-25
forum: General Help
---

### Post by Nexusx6 on 2017-12-25
Hello,

I've fought through a lot of problems with getting my Nvidia 1070ti to work on Ubuntu having tried 16.04, 17.04 and 17.10 and even trying Fredora 27. Every time I get close, my attempt dies when I'm installing the drivers and it always seems to be a kernel oops. The fact that it's happen even across distro's really makes this seem like a problem with the 4.13 kernel but I really don't know what to do from here. I'm a data scientist, and really, really need to CUDA and the drivers to do my job, so any help would really help out.

I made a similar post on launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-384/+bug/1740053") where various logs are also posted, but the gist of it is that the console gets to this point:

```
Not creating home directory `/'.
Loading new nvidia-384-384.90 DKMS files...
Building for 4.13.0-21-generic
Building for architecture x86_64
Building initial module for 4.13.0-21-generic
Error! Bad return status for module build on kernel: 4.13.0-21-generic (x86_64)
Consult /var/lib/dkms/nvidia-384/384.90/build/make.log for more information.
Setting up g++ (4:7.2.0-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up bbswitch-dkms (0.8-4ubuntu1) ...
Loading new bbswitch-0.8 DKMS files...
Building for 4.13.0-21-generic
Building initial module for 4.13.0-21-generic

Progress: [ 95%] [#######################################################...]
```

Then hangs at the 95% mark for minutes before Ubuntu/Fedora detects a crash and the install aborts, leaving me with this partial-install that APT complains about for a while.

Again, any help would be really appreciated

***[Edit]***
Some details I failed to add or point out. I've tried getting these drivers working on: 
  * vanilla Ubuntu 17.10/17.04 (Wayland off)
  * mini/netboot Ubuntu 17.10 (Wayland off)
  * Ubuntu MATE 17.10 (netboot)
  * Fedora 27

My video card is a Nvidia 1070ti and I'm dual booting with Windows 10. I've had no issue with the video card on the Windows 10 side. I'm posting this from a 17.10 netboot install.

```
$ lspci | grep NVIDIA
01:00.0 VGA compatible controller: NVIDIA Corporation GP104 (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)
```

---

### Post by Yellow Pasque on 2017-12-26
Since this is a desktop, is there a reason you're using bbswitch?
Have you tried turning off Hyperthreading and C-states in the BIOS just to make sure they're not the culprit? (and you're not OC'ing, correct?)

---

### Post by stepheny on 2017-12-26
Non of the nVidia proprietary drivers work with Wayland at the moment. You should purge all nVidia drivers and use the open source Nouveau driver for the time being. Or use Ubuntu on Xorg.

---

### Post by Nexusx6 on 2017-12-26
> **Temüjin said:**
> Since this is a desktop, is there a reason you're using bbswitch?
Have you tried turning off Hyperthreading and C-states in the BIOS just to make sure they're not the culprit? (and you're not OC'ing, correct?)

I'm not sure what bbswitch is to be honest. I didn't purposefully install it, so it must have came along as a dependency to something

[QUOTE=stepheny]Non of the nVidia proprietary drivers work with Wayland at the moment. You should purge all nVidia drivers and use the open source Nouveau driver for the time being. Or use Ubuntu on Xorg.[/QUOTE]

I'll edit my original post because I forgot to mention that. So I've tried installing the drivers on X.org when using a vanilla install, and already tried this with Ubuntu MATE and Fedora, so I'm pretty sure my situation isn't tied to the known GUI problem.

---

### Post by Nexusx6 on 2017-12-26
I found someone with who had a seemingly similar problem [here]("https://ubuntuforums.org/showthread.php?t=2324360"). The solution is found on the Nvidia forums where [someone points out ]("https://devtalk.nvidia.com/default/topic/936239/linux/-355-xx-370-23-ubuntu-16-04-all-kernel-version-stucks-while-building-dkms-module/post/5189999/#5189999") that the NOD32 Antivirus program was trying to protect his kernel and kept DKMS from compiling it. This isn't a solution on my part since I don't run an antivirus, but I thought I'd point it out in case it's relevant.

---

### Post by Yellow Pasque on 2017-12-26
You didn't answer these questions:
Have you tried turning off Hyperthreading and C-states in the BIOS just to make sure they're not the culprit? (and you're not OC'ing, correct?)

---

### Post by Nexusx6 on 2017-12-26
C-states are off but Hyper-threading is on and no OC. Every time I try to install the drivers I end up with an OS that has no working video drivers and end up going through a reinstall, so I'm hesitant to try a long shot attempt :/

---

### Post by Yellow Pasque on 2017-12-26
*Shrug* Well, something seems to be unstable on your system if it's complaining about "invalid opcode" and "bad swap file" entries. I'd be turning off any unnecessary CPU features and running memtest to start.

---

### Post by Nexusx6 on 2017-12-26
Good eye. I thought the RAM might have been the culprit because the first motherboard I ordered for this rig came with a defective NIC, but also only saw one of the two RAM sticks. I just ran memtest though, and everything came back with a okay. Worth pointing out that memtest wasn't an option from my GRUB menu or from the netboot live cd GRUB menu, so I ran it on 12 gigs with 1 pass.

Also, I did a check through BIOS to see if there was any overclocking settings or anything going on. X.M.P was enabled which I shut off before running memtest. It's possible X.M.P. was creating some instability that I didn't catch on memtest with it off. Any other diagnostics you think I should run?

---

### Post by Yellow Pasque on 2017-12-26
I don't have any other suggestions if you've tried multiple distros/kernels (and it looks like your BIOS is updated).
The HT thing was a long shot, but I was not pulling it out of thin air or anywhere else: [https://lists.debian.org/debian-devel/2017/06/msg00308.html](https://lists.debian.org/debian-devel/2017/06/msg00308.html)
Or, instead of disabling HT, you could try to use updated CPU microcode, i.e. install 'intel-microcode' package.

---

### Post by Nexusx6 on 2017-12-31
Small update: I've replaced the 1070 ti with a 970 GTX and everything works perfectly fine, including installing the nvidia-384 drivers. For whatever reason, it's this particular card that keeps the drivers from being installed. I ordered a new one from a different brand hoping that somehow, some kind of hardware fault was causing the issue and a different 1070 ti will work, but we'll see.

---

### Post by mc4man on 2017-12-31
bbswitch is a dependency of nvidia-prime which is a recommend of all packaged nvidia drivers. Probably not your issue but can be removed along with nvidia-prime (or not installed at all if using a --no-install-recommends apt option

Seeing as though nvidia 10 series cards are new (& assuming 1070 is very new) it may be a while to get linux support. 
For packaged driver try the driver ppa - [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

If new card doesn't work with ppa packages  look into installing latest nvidia linux drivers directly via the nvidia .run file . Search for instructions and caveats concerning that. If that fails file an issue on the nvidia site.

---

### Post by mc4man on 2017-12-31
> Consult /var/lib/dkms/nvidia-384/384.90/build/make.log for more information
Did you ever read that log?

---

