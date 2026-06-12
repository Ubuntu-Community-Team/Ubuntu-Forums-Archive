---
title: "Screen Color Saturation Quick Qestion"
date: 2019-07-27
forum: General Help
---

### Post by roiikkata on 2019-07-27
Hi guys!

Quick question; do the new Ati Radeon drivers allow for screen "saturation" adjustment? Catalyst Control Center style?

---

### Post by QIII on 2019-07-27
Which new driver?

ATI was bought by AMD and no longer exists.

Do you mean the open source Radeon driver?

---

### Post by roiikkata on 2019-07-27
The AMD-GPU driver I believe it is.

And thanks for the update about ATI and AMD. I have a i7 HP Elitebook so it's rather in-between generations, yes.

---

### Post by QIII on 2019-07-27
What model GPU does that use?

---

### Post by roiikkata on 2019-07-27
A Radeon HD 7500M series

I wouldn't mind troubleshooting I just don't have Ubuntu MATE (as I usually use) installed right now since this driver issue.
This has actually been keeping me from installing Ubuntu on it ..

Any hope?

---

### Post by QIII on 2019-07-27
I do not believe AMDGPU supports your GPU.  AMDGPU requires GPUs with 2nd gen GCN (Graphics Core Next) architecture -- GCN 1.1.

I don't think anything prior to the HD 7700 series used GCN architecture, and that was GCN 1.0.

There are a couple of things to consider here:  If your machine has an i7, then there is an Intel GPU on die.  You likely have a dedicated AMD GPU.  For your machine to use the AMD GPU, you will have to disable/blacklist the Intel GPU via your BIOS settings.

When Ubuntu installs, the installer checks for whether the GPU is supported by AMDGPU and, if so, uses the amdgpu module in the kernel.  Otherwise, the radeon module is used.  Unless AMDGPU is active, you cannot install the proprietary AMDGPU-PRO overlay.

Would you please post the results of 

```
lsmod | grep amdgpu
```

and

```
lsmod | grep radeon
```

so we can see if either is loaded?

---

### Post by roiikkata on 2019-07-27
Got it! And sure, let me get an install going. Un momento

---

### Post by roiikkata on 2019-07-27
lsmod | grep amdgpu

returns me with no result



lsmod | grep radeon

```

radeon               1458176  10
i2c_algo_bit           16384  1 radeon
ttm                   110592  1 radeon
drm_kms_helper        172032  1 radeon
drm                   458752  6 drm_kms_helper,radeon,ttm

```

---

### Post by cruzer001 on 2019-07-27
Not all EliteBooks have switchable graphics, some older models are hardwired and see just the external one.  Check for options with:
```
lspci -k | grep -A 2 -i "VGA"
```
If you have a switchable model you will see both Intel and Radeon.  Then to add to the confusion their is dynamic and fixed, again depends on the model.

[https://support.hp.com/bg-en/document/c03048374](https://support.hp.com/bg-en/document/c03048374)

---

### Post by roiikkata on 2019-07-27
Hardwired huh. So there wouldn't be a way around it not involving soldering. And that'd be if I even knew how to fix it that way.

I do know that when I opened up the service/access panel a bit ago to do some other work that the heatsink tubing crosses over a second chip which has a smaller heatsink on it that might be the GPU Mr. Q the Third here is talking about .. [-o<

I'm hoping it is. And then hoping the AMDGPU-PRO features include the color controls Catalyst Control Center does.


grep amdgpu turned up nothing which is my guess that AMDGPU won't install. And the only black/whitelisting I've seen is through custom BIOSes. Possibly a way to enable it in grub? I'm looking into it now ..

---

### Post by cruzer001 on 2019-07-27
CCC or grub will not help if its not supported on the mother board.  I take it that the above command shows only one.

---

