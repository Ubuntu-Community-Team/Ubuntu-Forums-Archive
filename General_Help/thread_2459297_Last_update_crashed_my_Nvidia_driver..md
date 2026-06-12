---
title: "Last update crashed my Nvidia driver."
date: 2021-03-15
forum: General Help
---

### Post by Robert_Gaines on 2021-03-15
When I updated Ubuntu Mate 20.10 today (3-15-2021), it crashed my Nvidia 460 driver. I don't know if I actually fixed the problem. I restarted in recovery mode with the previous version and fixed broken packages. When I ran Software Update, it said there were no updates. I don't know if I just booted up in the previous version. It wants me to delete the other files, and I'm not going to do that until I know I'm fine. I did rebuild the 460 driver in apt just before I restarted in the recovery mode, but the resolution was 640x480 so I restarted in recovery mode with the previous version. I don't know if when I continued booting if it loaded the newest install or the version I started up recovery mode in. You probably shouldn't allow the update of both the video driver and a major update of the OS at the same time. It looks fine now, but I don't know if I'm in the other previous update version or if I'm stuck in it until I reinstall the OS. It's a serious pain in the ass to have the video driver compiling crash in an update, and you end up being stuck with a corrupted driver.It should just revert back the the previous version of the driver if there is a problem with the compiling process. I mean, losing the video driver is down right scary!

---

### Post by daniewicz on 2021-03-15
The latest version of the nvidia driver is 5.8.0-44

---

### Post by CelticWarrior on 2021-03-15
> **daniewicz said:**
> The latest version of the nvidia driver is 5.8.0-44

No, that's the kernel version, nothing to do with Nvidia drivers.

---

### Post by daniewicz on 2021-03-15
Yes you are correct.

Driver is  460.39

Could it be that the updated kernel is causing the problem?

---

### Post by Autodave on 2021-03-15
Yes it could especially if you are using a 5.08 kernel.  I had all sorts of problems and went back to the 5.04.

---

### Post by lordgallen on 2021-03-15
I am on 5.8.0-45 and there was also an update to nvidia drivers, and all is well.

---

### Post by daniewicz on 2021-03-15
I am on 5.8.0-44-generic with no problem.

---

### Post by siuda on 2021-03-16
I do have similar problem with last update (3-15-2021), but with nvidia-driver-390 (390.141). Also on Ubuntu MATE.

The problem seems to be with kernel version 5.8.0-45. With 5.8.0-44 everything is fine like before.

For the kernel 5.8.0-45 (newer) the driver seems to be there but is not working with it's good quality. I can see the proprietary driver selected in *Control Panel* -> *Additional Drivers*, however I can't see nvidia being listed with ```
[sudo] lshw -c video | grep configuration
```

The resolution is lower and the games are not working.

I can switch to kernel 5.8.0-44 with grub and use my system like before. Can't use the newer kernel though...

---

### Post by daniewicz on 2021-03-16
5.8.0-45-generic update this morning and got the low resolution problem.

5.8.0-45-generic update this afternoon and all is well again.

---

### Post by Robert_Gaines on 2021-03-16
I used Grub Customizer to boot into 5.8.0-44-generic for now as I'm sick with something. It's not a long term solution.

---

### Post by siuda on 2021-03-17
OK, just installed some new driver kernel modules from the updates and everything seems to be fine now with newer kernel 5.8.0-45. Bug for nvidia driver 390.141 seems to be fixed.

---

### Post by Robert_Gaines on 2021-03-18
Has there been a fix or a work around for this problem yet? Will the Nvidia video driver work in a fresh install of Ubuntu? I don't want to reinstall Ubuntu just to find my video card doesn't work.

---

### Post by daniewicz on 2021-03-18
The new driver kernel modules have resolved this problem.

---

### Post by Robert_Gaines on 2021-03-20
I used Grub Customizer to return Grub to normal loading settings. I am running 5.8.0-45-generic with normal video settings, so I do believe that this issue is now solved.

---

### Post by TheFu on 2021-03-21
I had a problem yesterday with the nvidia driver after patching - I patch weekly.
The easy solution that worked was
```
sudo ubuntu-drivers autoinstall
```
then reboot.

Kernel: 5.4.0-67-generic

```
$ dpkg -l 'nvidia*' |egrep '^ii'
ii  nvidia-compute-utils-460-server  460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA compute utilities
ii  nvidia-dkms-460-server           460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA DKMS package
ii  nvidia-driver-460-server         460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA Server Driver metapackage
ii  nvidia-kernel-common-460-server  460.32.03-0ubuntu0.18.04.1 amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-460-server  460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA kernel source package
ii  nvidia-prime                     0.8.8.2                    all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                  440.82-0ubuntu0.18.04.1    amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-460-server          460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA Server Driver support binaries

```
are working.  1024x768 resolution is bad. ;)

---

### Post by daniewicz on 2021-04-12
This problem is back again with the most recent kernel update on ubuntu 20.04 :eek:

---

### Post by heethoofd27 on 2021-04-14
I think I am having the same problem. Though I am getting a black screen when booting up, likely because I am using a laptop with hybrid graphics.
Currently I can login by selecting kernel 5.8.0-45-generic in GRUB but I would like to solve this.
Have you managed to find a solution?

---

### Post by daniewicz on 2021-04-14
not yet

---

