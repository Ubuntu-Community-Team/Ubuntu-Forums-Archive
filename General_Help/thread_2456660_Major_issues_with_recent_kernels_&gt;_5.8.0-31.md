---
title: "Major issues with recent kernels &gt; 5.8.0-31"
date: 2021-01-16
forum: General Help
---

### Post by vleermuis on 2021-01-16
Hi all,

I am recently having a lot of problems with any new kernel release since 5.8.0-31. The only way I can still work with my system is by booting into 5.8.0-31 - no other kernel up to the most recently published 5.8.0-38 will work.

Here's some info on my setup:
[LIST]
[*]I have a Thinkpad T480 with dedicated NVidia graphics 
[*]I am running Windows 10 and Kubuntu in Dual Boot 
[*]Kubuntu Version is 20.10 
[*]My harddrive is encrypted 
[/LIST]

I am facing several issues when booting into a newer kernel. First of all, when I have my Thinkpad in the Dock (I have two external monitors connected), I cannot enter the password for decryption with my external keyboard. It seems the keyboard is not recognized at this point (although it is when GRUB shows up where I select what to boot).

Second, after decrypting, no login screen shows up - I have to switch to the terminal mode (ctrl+alt+f2) to login and then startx manually.
Regarding this issue, my first suspicion was something with the nvidia drivers, since I read a lot about them causing problems, so I switched to using the onboard Intel graphics, but it didn't help.
```
[FONT=monospace][COLOR=#000000]$ prime-select query [/COLOR]
intel[/FONT]
```

And last but maybe not least, I have network issues. Apparently, the wifi adapter is no longer recognized. Here's the output I get for the adapter:

```
$ sudo lshw -c net

*-network UNCLAIMED 
description: Network controller
product: Wireless 8265 / 8275
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 78
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:dd100000-dd101fff
```

So the only way to go online is via ethernet cable, at least this works.

I am a bit lost about where to start looking for the cause of all these issues. I hope you can help. Thanks.

---

### Post by grahammechanical on 2021-01-16
On this forum we have seen several posts regarding problems that occurred after an update in which the update brought in the Linux 3.8 kernel. I do not think I will be contradicted if I say that if you have a working kernel you can boot into, then use that as a solution until a kernel upgrade fixes the problem.

I do advise caution. A kernel update through Software Updater will remove an older kernel so that only 2 kernels are present. If both those kernels are broken then you have a bigger problem. Doing Update/Upgrade from the terminal does not remove older kernels. We need to run autoremove to get rid of them but we may not want to do that at the present time. Not until we have a working Linux 3.8 kernel. 

I am still on kernel 5.4 and still getting updates to it. The moment I get a 5.8 kernel I will stop using Software Updater until I am confident that the 5.8 kernel works. Having said that, I do have installs of 20.10 & 21.04 (development) with the 5.8 kernel and there is not a problem. I think older hardware that I have does not trip up the 5.8 kernel.

Regards

---

### Post by CelticWarrior on 2021-01-17
Only a small set of hardware that have been affected by the 5.8 upgrade. I had to deal with it recently for a customer. Only one out of 3 of their Intel CPU and GPU based computers of different vintages was affected. Indeed it was the newer one, a miniPC with a Celeron. But, funny thing, I'm right now typing from a very similar, only slightly newer, Celeron based miniPC running fine with dreaded 5.8 kernel.

---

### Post by vleermuis on 2021-01-17
Thank you. My initial reaction when these issues first occured (with the 5.8.0.33 I think) was the same, just stay on the one that works for now, and wait until another one comes out that fixes the issues. But since then, another four or so updates came out and none of them seems to fix anything. How can these kernels still be broken? This is why I started to suspect there may be some other problems with my installation that I should look into.

Oh and thanks for your advice, I do my updates solely via terminal, so I guess I'm good. I just have to scroll deeper and deeper in the kernel list of GRUB. ;) Maybe I should just deactivate or uninstall the broken ones.

> Having said that, I do have installs of 20.10 & 21.04 (development) with the 5.8 kernel and there is not a problem.
By the way, I made a mistake in my original post, I am indeed using Kubuntu 20.10 already.

---

### Post by jeremy31 on 2021-01-17
Check in terminal ```
dpkg -l | grep linux-modules-extra
```
See if the versions are missing for the kernels that have issues

---

### Post by vleermuis on 2021-01-18
> **jeremy31 said:**
> Check in terminal ```
dpkg -l | grep linux-modules-extra
```
See if the versions are missing for the kernels that have issues

Hmm indeed, they are missing for all of the kernels that cause issues for me apparently:

```
[FONT=monospace][COLOR=#000000]$ dpkg -l | grep linux-modules-extra [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-20-generic           4.15.0-20.21                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-23-generic           4.15.0-23.25                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-24-generic           4.15.0-24.26                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-29-generic           4.15.0-29.31                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-30-generic           4.15.0-30.32                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-32-generic           4.15.0-32.35                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-33-generic           4.15.0-33.36                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-34-generic           4.15.0-34.37                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-36-generic           4.15.0-36.39                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-38-generic           4.15.0-38.41                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-39-generic           4.15.0-39.42                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-42-generic           4.15.0-42.45                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-43-generic           4.15.0-43.46                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-44-generic           4.15.0-44.47                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-45-generic           4.15.0-45.48                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-46-generic           4.15.0-46.49                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-47-generic           4.15.0-47.50                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-48-generic           4.15.0-48.51                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-50-generic           4.15.0-50.54                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-51-generic           4.15.0-51.55                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-52-generic           4.15.0-52.56                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.15.0-54-generic           4.15.0-54.58                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-4.18.0-25-generic           4.18.0-25.26                                amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.0.0-20-generic            5.0.0-20.21                                 amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.0.0-21-generic            5.0.0-21.22                                 amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.0.0-23-generic            5.0.0-23.24                                 amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.0.0-25-generic            5.0.0-25.26                                 amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.0.0-27-generic            5.0.0-27.28                                 amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.0.0-29-generic            5.0.0-29.31                                 amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.0.0-32-generic            5.0.0-32.34                                 amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.3.0-19-generic            5.3.0-19.20                                 amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP [/COLOR]
ii  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.3.0-23-generic            5.3.0-23.25                                 amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.3.0-24-generic            5.3.0-24.26                                 amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-29-generic            5.4.0-29.33                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-31-generic            5.4.0-31.35                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-33-generic            5.4.0-33.37                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-37-generic            5.4.0-37.41                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-39-generic            5.4.0-39.43                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-40-generic            5.4.0-40.44                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-42-generic            5.4.0-42.46                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-45-generic            5.4.0-45.49                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-47-generic            5.4.0-47.51                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.4.0-52-generic            5.4.0-52.57                                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.8.0-25-generic            5.8.0-25.26                                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.8.0-26-generic            5.8.0-26.27                                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.8.0-28-generic            5.8.0-28.30                                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP [/COLOR]
rc  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.8.0-29-generic            5.8.0-29.31                                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP [/COLOR]
ii  [COLOR=#ff5454]**linux-modules-extra**[/COLOR][COLOR=#000000]-5.8.0-31-generic            5.8.0-31.33                                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP[/COLOR]
[/FONT]
```

So what does that tell me exactly? I guess I will have to install some additonal packages?

---

### Post by mastablasta on 2021-01-19
> **vleermuis said:**
> 
So what does that tell me exactly? I guess I will have to install some additonal packages?

looks like it. you said:

> [COLOR=#000000]The only way I can still work with my system is by booting into 5.8.0-31 - no other kernel up to the most recently published 5.8.0-38 will work.[/COLOR]

the extra module are missing from then onwards. 

what happens if you:
```
[FONT=Consolas]sudo apt install linux-generic[/FONT]
```

it should pull in all the necessary modules.

Another version:
```
sudo apt install --reinstall linux-image-generic
```

---

### Post by bcschmerker on 2021-01-19
**I haven't attemped Packages LinUX-*-5.8.0-*nn*-generic to date on my Hot Rod gPC, which was running reliably on 5.4.0-62-generic until it stopped POST with a "Keyboard error or no keyboard present" error** (see "[Hot Rod gPC down, need motherboard](https://ubuntuforums.org/showthread.php?t=2456551)").  I's last on ubuntu® 20.04.1-LTS Focal and hadn't used Metapackages linux-*-generic-20.04-lts-edge as of 15 January 2021 (last successful boot).

---

### Post by vleermuis on 2021-01-20
> **mastablasta said:**
> 
what happens if you:
```
sudo apt install linux-generic
```

it should pull in all the necessary modules.

Another version:
```
sudo apt install --reinstall linux-image-generic
```

Now this is strange, here's what I got:

```
$ sudo apt install linux-generic                   
Reading package lists... Done
Building dependency tree        
Reading state information... Done
linux-generic is already the newest version (5.8.0.31.36).
```

and

```
$ sudo apt install --reinstall linux-image-generic
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reinstallation of linux-image-generic is not possible, it cannot be downloaded.
```

But as you said

> **mastablasta said:**
> the extra module are missing from then onwards.

I then tried to manually install exactly that, so I did

```
$ sudo apt install linux-modules-extra-5.8.0-38-generic
```

and

```
$ sudo apt install linux-headers-5.8.0-38-generic
```(since the output of the first told me so)

, rebooted, and it seems I've got a working system again. :)

Strange that these modules were missing in the first place...

---

### Post by mastablasta on 2021-01-21
it is strange. did you maybe add some driver PPA or patch kernel with driver? or maybe nvidia drivers are messing it up. but i have seen a couple similar posts where kernel is the issue.

linux image generic should be meta package and pull in the correct modules:
> [COLOR=#000000][FONT=&quot]Reinstallation of linux-image-generic is not possible, it cannot be downloaded.[/FONT][/COLOR]

i wonder if maybe that is the whole reason why people have nvidia issues with 5.8 - additional modules are not pulled in during upgrade.

---

### Post by vleermuis on 2021-01-21
> **mastablasta said:**
> it is strange. did you maybe add some driver PPA or patch kernel with driver?

Umm no, I don't see any specific PPA for the nvidia drivers, I guess I installed them the "regular" way. What do you mean by "patch kernel with driver"?

Another kernel update came in today... The next reboot will show if history repeats. ;)

---

### Post by vleermuis on 2021-01-22
History repeats indeed - just got a fresh update to 5.8.0-40 yesterday and guess what - same issues. I don't think I should have to manually install these module-extra and headers packages for each new kernel update.
Any ideas?

---

### Post by Impavidus on 2021-01-23
Indeed, you shouldn't need to. AFAIK, the image package and the modules-extra package are pulled in by the same metapackage, so something funny must be happening. Let's look at a list of all of those packages you've installed:```
dpkg --list | grep 'linux-' | grep -v '^rc'
```

---

### Post by vleermuis on 2021-01-28
Sure, let's have a look:

```
[FONT=monospace][COLOR=#000000]$ dpkg --list | grep 'linux-' | grep -v '^rc' [/COLOR]
ii  binutils-x86-64-linux-gnu                       2.35.1-1ubuntu1                             amd64        GNU binary utilities, for x86-64-linux-gnu target 
ii  linux-base                                      4.5ubuntu4                                  all          Linux image base package 
ii  linux-firmware                                  1.190.2                                     all          Firmware for Linux kernel drivers 
ii  linux-generic                                   5.8.0.31.36                                 amd64        Complete Generic Linux kernel and headers 
ii  linux-headers-5.8.0-31                          5.8.0-31.33                                 all          Header files related to Linux kernel version 5.8.0 
ii  linux-headers-5.8.0-31-generic                  5.8.0-31.33                                 amd64        Linux kernel headers for version 5.8.0 on 64 bit x86 SMP 
ii  linux-headers-5.8.0-38-generic                  5.8.0-38.43~20.04.1                         amd64        Linux kernel headers for version 5.8.0 on 64 bit x86 SMP 
ii  linux-headers-5.8.0-40-generic                  5.8.0-40.45~20.04.1                         amd64        Linux kernel headers for version 5.8.0 on 64 bit x86 SMP 
ii  linux-headers-generic                           5.8.0.31.36                                 amd64        Generic Linux kernel headers 
ii  linux-hwe-5.8-headers-5.8.0-38                  5.8.0-38.43~20.04.1                         all          Header files related to Linux kernel version 5.8.0 
ii  linux-hwe-5.8-headers-5.8.0-40                  5.8.0-40.45~20.04.1                         all          Header files related to Linux kernel version 5.8.0 
ii  linux-image-5.3.0-23-generic                    5.3.0-23.25                                 amd64        Signed kernel image generic 
ii  linux-image-5.8.0-31-generic                    5.8.0-31.33                                 amd64        Signed kernel image generic 
ii  linux-image-5.8.0-38-generic                    5.8.0-38.43~20.04.1                         amd64        Signed kernel image generic 
ii  linux-image-5.8.0-40-generic                    5.8.0-40.45~20.04.1                         amd64        Signed kernel image generic 
ii  linux-image-generic                             5.8.0.31.36                                 amd64        Generic Linux kernel image 
ii  linux-libc-dev:amd64                            5.8.0-31.33                                 amd64        Linux Kernel Headers for development 
ii  linux-modules-5.3.0-23-generic                  5.3.0-23.25                                 amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP 
ii  linux-modules-5.8.0-31-generic                  5.8.0-31.33                                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP 
ii  linux-modules-5.8.0-38-generic                  5.8.0-38.43~20.04.1                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP 
ii  linux-modules-5.8.0-40-generic                  5.8.0-40.45~20.04.1                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP 
ii  linux-modules-extra-5.3.0-23-generic            5.3.0-23.25                                 amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP 
ii  linux-modules-extra-5.8.0-31-generic            5.8.0-31.33                                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP 
ii  linux-modules-extra-5.8.0-38-generic            5.8.0-38.43~20.04.1                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP 
ii  linux-modules-extra-5.8.0-40-generic            5.8.0-40.45~20.04.1                         amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP 
ii  linux-modules-nvidia-455-generic-hwe-20.04-edge 5.8.0-40.45~20.04.1                         amd64        Extra drivers for nvidia-455 for the generic flavour (dummy transitional package) 
ii  linux-modules-nvidia-460-5.8.0-38-generic       5.8.0-38.43~20.04.1                         amd64        Linux kernel nvidia modules for version 5.8.0-38 
ii  linux-modules-nvidia-460-5.8.0-40-generic       5.8.0-40.45~20.04.1                         amd64        Linux kernel nvidia modules for version 5.8.0-40 
ii  linux-modules-nvidia-460-generic-hwe-20.04-edge 5.8.0-40.45~20.04.1                         amd64        Extra drivers for nvidia-460 for generic-hwe-20.04-edge 
ii  linux-sound-base                                1.0.25+dfsg-0ubuntu5                        all          base package for ALSA and OSS sound systems
[/FONT]
```

---

### Post by Impavidus on 2021-01-28
OK, your linux-generic, linux-headers-generic and linux-image-generic are all there, but are stuck at version 5.8.0.31. Normally those are the packages that pull in the new kernel. In your case, the new kernel (linux-image-5.8.0-41-generic) is pulled in by linux-modules-nvidia-460-hwe-20.04-generic-edge, but this doesn't pull in the linux-modules-extra-*-generic package.

So the thing to do is to get linux-generic unstuck. What do you get from```
apt-cache policy linux-generic linux-image-generic linux-headers-generic
```

---

### Post by vleermuis on 2021-01-28
Yeah seems like it...

```
[FONT=monospace][COLOR=#000000]$ apt-cache policy linux-generic linux-image-generic linux-headers-generic [/COLOR]
linux-generic: 
  Installed: 5.8.0.31.36 
  Candidate: 5.8.0.31.36 
  Version table: 
 *** 5.8.0.31.36 100 
        100 /var/lib/dpkg/status 
     5.4.0.65.68 500 
        500 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages 
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages 
     5.4.0.26.32 500 
        500 http://de.archive.ubuntu.com/ubuntu focal/main amd64 Packages 
linux-image-generic: 
  Installed: 5.8.0.31.36 
  Candidate: 5.8.0.31.36 
  Version table: 
 *** 5.8.0.31.36 100 
        100 /var/lib/dpkg/status 
     5.4.0.65.68 500 
        500 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages 
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages 
     5.4.0.26.32 500 
        500 http://de.archive.ubuntu.com/ubuntu focal/main amd64 Packages 
linux-headers-generic: 
  Installed: 5.8.0.31.36 
  Candidate: 5.8.0.31.36 
  Version table: 
 *** 5.8.0.31.36 100 
        100 /var/lib/dpkg/status 
     5.4.0.65.68 500 
        500 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages 
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages 
     5.4.0.26.32 500 
        500 http://de.archive.ubuntu.com/ubuntu focal/main amd64 Packages
[/FONT]
```

How do I get it unstuck?

---

### Post by Impavidus on 2021-01-29
I see only focal sources. Can you show the contents of your sources.list?```
cat /etc/apt/sources.list
```

---

### Post by vleermuis on 2021-01-30
Huh you're right, since I'm already on 20.10 this should be gorilla right... Strange. I don't remember when exactly I upgraded from 20.04, I think not long after it came out. Does an upgrade not automatically update my sources?
Here's the list, indeed only focal stuff (and commented bionic entries, this is the version I set my laptop up with in the first place).

```
[FONT=monospace][COLOR=#000000]$ cat /etc/apt/sources.list [/COLOR]
# deb cdrom:[Kubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main multiverse restricted universe 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to 
# newer versions of the distribution. 
deb http://de.archive.ubuntu.com/ubuntu/ focal main restricted 
# deb-src http://de.archive.ubuntu.com/ubuntu/ bionic main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://de.archive.ubuntu.com/ubuntu/ focal-updates main restricted 
# deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb http://de.archive.ubuntu.com/ubuntu/ focal universe 
deb http://de.archive.ubuntu.com/ubuntu/ focal-updates universe 
# deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  
## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb http://de.archive.ubuntu.com/ubuntu/ focal multiverse 
deb http://de.archive.ubuntu.com/ubuntu/ focal-updates multiverse 
# deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-updates multiverse 

## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb http://de.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse 
# deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
# deb http://archive.canonical.com/ubuntu bionic partner 
# deb-src http://archive.canonical.com/ubuntu bionic partner 

deb http://security.ubuntu.com/ubuntu focal-security main restricted 
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted 
deb http://security.ubuntu.com/ubuntu focal-security universe 
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe 
deb http://security.ubuntu.com/ubuntu focal-security multiverse 
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
[/FONT]
```

---

### Post by Impavidus on 2021-01-30
A release upgrade does update your software sources. It seems that shortly after you installed the kernel upgrade to 5.8.0-31 on your well-functioning groovy system, your software sources were somehow reset to focal. Maybe something going wrong with a backup routine, like an accidental restore?

It looks like your system was a well-functioning 20.10 system until after the release of 5.8.0-31, so most packages must be the proper versions for 20.10. I don't think many packages have been replaced by their 20.04 versions, as those typically have lower version numbers. My suggestion is that you backup your documents and get a 20.10 live disk ready (just in case), then change your software sources to groovy by editing your sources.list. Then see what upgrades the package manager wants to install.

---

### Post by bcschmerker on 2021-02-02
**If it helps with the confusion, I did some cherrypicking with 20.04.1-LTS on an *e*machines®/ac*e*r® EL1210-09** (Acer Computer Corp. DA078L: Advance Micro Devices Athlon 64 LE-1620; nVIDIA nForce 780a MCP, C77 geForce GPU in northbridge by-passed with GF119 GPU in msi N610GT-1GD5-LP).  I selected the Metapackages linux-{image,modules,modules-extra,modules-nvidia-390,headers,tools}-generic-hwe-20.04 (which pulled in appropriate Depends for just-released Kernel versions) , and the Packages nvidia-settings and libnvidia-{common,compute,decode}-390 from Synaptic; nvidia-dkms-390 proved unnecessary, and the EL1210 is stable, excepting a buggy OpenLP 2.9.2-1 (unrelated issue).

[@vleermuis](https://ubuntuforums.org/member.php?u=2155836)  **Reading Post 14, I discovered a Metapackage goof: linux-modules-nvidia-460-generic-hwe-20.04-edge instead of linux-modules-nvidia-460-generic.**  The HWE and HWE-Edge Kernel updates are on a different schedule from the base Kernel updates.  Bleeding-edge Kernel users should have the Metapackages linux-headers-generic-hwe-20.04-edge, linux-image-generic-hwe-20.04-edge, linux-modules-extra-generic-hwe-20.04-edge, (optional) linux-tools-generic-hwe-20.04-edge, and (specific to Kepler and newer geForce and QUADRO) linux-modules-nvidia-460-generic-hwe-20.04-edge, thereby synchronizing the new Kernel package downloads.

---

### Post by Impavidus on 2021-02-03
vleermuis is on Ubuntu 20.10, where hwe-20.04-edge and the normal kernels both point to kernel 5.8. This mixup of the normal version and the hwe-20.04-edge version is somewhat peculiar, but not really a problem.

How do I know? linux-generic is at version 5.8.0.31.36. On 20.04 linux-generic always stays at 5.4.0.* and only hwe-20.04 and hwe-20.04-edge move to 5.8.0.*. This system must have used the 20.10 sources in the past, but somehow reverted to 20.04 sources.

---

### Post by vleermuis on 2021-02-16
Sorry, I totally forgot to answer.

@[**[COLOR=#000000]Impavidus[/COLOR]**]("https://ubuntuforums.org/member.php?u=1417721"): I followed your suggestions editing my sources list to all groovy sources. A lot of updates came in afterwards, and I do not seem to have any issues since then. There has not been another kernel update since, so I will wait for that before fully declaring this solved, but I think it's very plausible that this was the problem. I also feel a bit stupid that I did not notice that all the sources were still focal ones. But now I have learned something new.

@[**[COLOR=#000000]bcschmerker[/COLOR]**]("https://ubuntuforums.org/member.php?u=609186"): Sorry I did not fully understand your post. Do you suggest I fix something with the nvidia packages too? If so, what exactly?

---

### Post by bcschmerker on 2021-02-18
[@vleermuis](https://ubuntuforums.org/member.php?u=2155836)  (-:  **Groovy?  I'm used to Focal.**  In which case, the Metapackages linux-*-generic are correct your system.  Ye can safely purge linux-modules-nvidia-*-hwe-20.04-edge and install linux-modules-nvidia-460-generic (which will drag in the appropriate Package linux-modules-nvidia-460-5.8.0-??-generic on the Groovy kernel-update schedule).

---

