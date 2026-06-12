---
title: "How do I report kernel bug in Ubuntu?"
date: 2022-01-19
forum: General Help
---

### Post by mapniv on 2022-01-19
Hello,
I faced a problem with kernel or one of drivers. When my device turns on I can see login screen. But when I log in I see something similar to static noise in TV. Using older kernel solves the issue. That's why I think it's a problem with kernel. Where should I report such a bug? Program called `ubuntu-bug' requires process id/package name.

---

### Post by deadflowr on 2022-01-19
You can report it to launchpad:[https://bugs.launchpad.net/ubuntu/+source/linux]("https://bugs.launchpad.net/ubuntu/+source/linux")

But out of curiosity, what driver do you think is of issue?
What kind of graphics card is in use?

If you're not sure what's what you might  look at posting some information.
You could use this: [https://github.com/UbuntuForums/system-info]("https://github.com/UbuntuForums/system-info")

It may be that your issue is well known and someone might be able to point you in a worthwhile direction.

---

### Post by mapniv on 2022-01-20
I found out that Ubuntu uses two kinds of kernels: stable ones and hardware enablement ones. The hardware enablement ones are latest versions and therefore less stable. HWE kernels (5.13.0-25-generic and 5.13.0-27-generic) do not work but 5.11.0-46-generic does.

> But out of curiosity, what driver do you think is of issue?
amdgpu

> What kind of graphics card is in use?
AMD Stoney [Radeon R2/R3/R4/R5 Graphics]

The following command: 'apt search amdgpu' returned following entries (I listed installed only):
xserver-xorg-video-amdgpu
  X.Org X server -- AMD display driver
libdrm-amdgpu1
  Userspace interface to amdgpu-specific kernel DRM services -- runtime

I would like to add that while the screen was showing static-noise-like patterns I was able to make a screenshot. It depicted my desktop as if nothing had happened. This means that X.Org isn't the cause.

EDIT:
I can see the login screen. I click on my username, enter the password and then it happens.

---

