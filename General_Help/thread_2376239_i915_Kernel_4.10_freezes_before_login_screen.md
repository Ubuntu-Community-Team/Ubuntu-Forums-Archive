---
title: "i915 Kernel 4.10 freezes before login screen"
date: 2017-10-31
forum: General Help
---

### Post by JoeGoldman on 2017-10-31
Hi Forum,

 Having a bit of an annoying issue.

 I recently got an XPS 15 9560 - first thing I did was re-install to Ubuntu 16.04 - trying to stick with LTS releases.

 First boot, install etc all go fine. The install media I have installs kernel 4.4, which loads a driver listed as i915_bpo in lshw -c video. After doing an apt upgrade, it installed kernel 4.10.0-37 (or -38 now). After installed, fresh reboot and no boot. Gets through the boot splash screen and just as its trying to load login screen it freezes. I can reboot into old kernel again without issue. I install nvidia-384 (this is a laptop with both intel and nvidia GPUs), and it defaults prime-select to nvidia so next boot into 4.10 is fine, but if I use prime-select to push it back to intel (on CLI, i've heard using nvidia-settings is even buggier), if I log out to force the change, it freezes. If I reboot, same symptom as before.

 When booted on nvidia drivers using nvidia GPU - I notice in lshw that driver has changed from i915_bpo to just i915.

 I also check dpkg --list and notice the driver is coming from package xserver-xorg-video-intel-hwe-16.04, so I add the 01.org repositories to apt, remove that package and install i915-4.6.3-4.4.0-dkms (and -source), reboot, set prime-select to intel, but still same problem.

 It seems no matter what driver im using I cant get Kernel 4.10 to boot with i915 as the GPU. My ultimate goal is to install bumblebee and only call on the nvidia GPU for graphics intensive apps but at the moment im running full time on nvidia which can hurt battery life.

I found this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1723174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1723174)

But suggestions in there don't appear to be helping me, and its since been marked as invalid.

Anyone got any ideas?

---

