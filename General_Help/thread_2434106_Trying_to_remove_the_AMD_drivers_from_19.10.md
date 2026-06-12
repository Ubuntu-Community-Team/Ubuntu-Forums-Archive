---
title: "Trying to remove the AMD drivers from 19.10"
date: 2019-12-30
forum: General Help
---

### Post by TheFuzz4 on 2019-12-30
So I've got my install of 19.10 running great.  My video card fan died so I pulled one of my AMD Vega's from my decommed mining rig and put it to work in my desktop :) So then I went to AMD and downloaded their driver package figured all was well.

Then I realized that AMD only releases drivers for LTS versions of Ubuntu and was like well crap of course I figured this out after I attempted to install the drivers.

So now here I am with a semi broken package system.  I cannot install updates right now because anytime I attempt to do anything I get 
```

sudo apt dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 amdgpu-dkms : Depends: amdgpu-core but it is not installed
 amdgpu-lib : Depends: amdgpu-core (= 19.30-934563) but it is not installed
 glamor-amdgpu : Depends: amdgpu-core but it is not installed
 gst-omx-amdgpu : Depends: amdgpu-core but it is not installed
 libdrm-amdgpu-common : Depends: amdgpu-core but it is not installed
 libdrm2-amdgpu:i386 : Depends: amdgpu-core:i386
 libdrm2-amdgpu : Depends: amdgpu-core but it is not installed
 libegl1-amdgpu-mesa:i386 : Depends: amdgpu-core:i386
 libegl1-amdgpu-mesa : Depends: amdgpu-core but it is not installed
 libgbm1-amdgpu:i386 : Depends: amdgpu-core:i386
 libgbm1-amdgpu : Depends: amdgpu-core but it is not installed
 libgl1-amdgpu-mesa-dri:i386 : Depends: amdgpu-core:i386
                               Recommends: libtxc-dxtn-s2tc0:i386 but it is not installable or
                                           libtxc-dxtn0:i386 but it is not installable
 libgl1-amdgpu-mesa-dri : Depends: amdgpu-core but it is not installed
                          Recommends: libtxc-dxtn-s2tc0 but it is not installable or
                                      libtxc-dxtn0 but it is not installable
 libglapi-amdgpu-mesa:i386 : Depends: amdgpu-core:i386
 libglapi-amdgpu-mesa : Depends: amdgpu-core but it is not installed
 libllvm9.0-amdgpu:i386 : Depends: amdgpu-core:i386
 libllvm9.0-amdgpu : Depends: amdgpu-core but it is not installed
 libwayland-amdgpu-client0:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-client0 : Depends: amdgpu-core but it is not installed
 libwayland-amdgpu-egl1:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-egl1 : Depends: amdgpu-core but it is not installed
 libwayland-amdgpu-server0:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-server0 : Depends: amdgpu-core but it is not installed
 mesa-amdgpu-va-drivers:i386 : Depends: amdgpu-core:i386
 mesa-amdgpu-va-drivers : Depends: amdgpu-core but it is not installed
 mesa-amdgpu-vdpau-drivers:i386 : Depends: amdgpu-core:i386
 mesa-amdgpu-vdpau-drivers : Depends: amdgpu-core but it is not installed
 xserver-xorg-amdgpu-video-amdgpu : Depends: amdgpu-core but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

I've tried everything that I can find for a solution for this and at this point sadly the only solution I can think of is to reinstall the desktop and I'd really rather not do that as I look at that as hitting it with a hammer instead of just hitting it with something simple :).

Thank you all for your help with this in advance.

---

### Post by CatKiller on 2019-12-30
What happens if you run *sudo apt --fix-broken install*?

---

### Post by QIII on 2019-12-30
When you first put in your AMD card, where you running any other driver -- say for NVIDIA?

Was the card working immediately after installing it?

AMDGPU is baked into the kernel now. You should not have needed to "install" anything.  You would only have had to make sure the module was loading.

You can test that right now by 

```
lsmod | grep amdgpu
```

My guess is it will be there, and the output of that command will look something like

```
amdgpu               3170304  38
amdchash               16384  1 amdgpu
amd_sched              24576  1 amdgpu
amdttm                110592  1 amdgpu
amdkcl                 28672  4 amdkfd,amd_sched,amdttm,amdgpu
drm_kms_helper        172032  1 amdgpu
drm                   401408  15 drm_kms_helper,amd_sched,amdttm,amdgpu,amdkcl
i2c_algo_bit           16384  2 igb,amdgpu

```

Perhaps less detail, since I have also added AMDGPU-PRO, which is the proprietary overlay.

---

### Post by TheFuzz4 on 2019-12-30
@catkiller yeah I've tried that with no love.
@QIII yeah I didn't realize it was baked in and yes I was running NVIDIA before.  Yeah the card worked right out of the bat

```

lsmod | grep amdgpu
amdgpu               4190208  110
amd_iommu_v2           20480  1 amdgpu
gpu_sched              32768  1 amdgpu
ttm                   106496  1 amdgpu
drm_kms_helper        184320  1 amdgpu
drm                   491520  15 gpu_sched,drm_kms_helper,amdgpu,ttm
i2c_algo_bit           16384  1 amdgpu

```
Right now I'm just trying to get it to where I can yank all of this amd stuff that it is trying to install but can't because of the fact that I don't have a LTS version of Ubuntu installed.  I'd just like to get back to a functioning package manager so if this involves nuking something to achieve this I'm all game.  I've attempted to remove every single package on this list of dependencies with no luck.

---

### Post by QIII on 2019-12-31
I don't know that the problem is that it is not an LTS.  I doubt that matters.  AMDGPU would have been in the kernel.

The issue is that you tried to add AMDGPU from the AMD site rather than just using what was already in the kernel and that messed with the Canonical repos.

Let me see what I can find to help you out.  Was it AMDGPU-PRO that you attempted to install?  *That* may not install on non-LTS releases.

---

### Post by QIII on 2019-12-31
First, uninstall the NVIDIA driver.  I'm not familiar with NVIDIA of late, so I'm not sure how to do that.

Then let's see if the uninstall script exists and try running that.

```
sudo amdgpu-pro-uninstall
```

---

### Post by TheFuzz4 on 2019-12-31
Ok got the NVIDIA stuff removed and when I run the uninstall it still throws out the error about needed packages.

---

### Post by Autodave on 2019-12-31
Did you restart the PC after purging the nVidia driver?

---

### Post by TheFuzz4 on 2019-12-31
Oh yeah I've been in this broken state now for a few weeks.  Apparently I thought I had removed all of the Nvidia stuff but it looks like its still hanging out in some forms but when trying to remove it, it just throws the broken packages error that started all of this.  LOL sigh

---

### Post by Bashing-om on 2019-12-31
TheFuzz4; Hello.

> 
I had removed all of the Nvidia stuff but it looks like its still hanging out in some forms but when trying to remove it,


what shows:
```

dpkg -l | grep -i nvidia
lsmod | grep nvidia
cat /var/log/gpu-manager.log

```

To remove all doubts, or point to a way forward.

[INDENT]all in the process
[/INDENT]

---

### Post by TheFuzz4 on 2020-01-02
So I finally just removed everything that was in that list of broken dependencies and even removed the things that they asked for and all is now well in the world.  Thank you all for your help with this and Happy New Year

---

### Post by Bashing-om on 2020-01-02
TheFuzz4' Yah !

Glad you got it all worked out :D

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

