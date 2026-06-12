---
title: "Ubuntu 16.04.1 LTS - Support and End of Life"
date: 2017-06-21
forum: General Help
---

### Post by tatonqek on 2017-06-21
Hi Everyone,

So I've been having some difficulty with understanding the update process for Ubuntu. I currently install from the Ubuntu 16.04.1 LTS ISO. I do not install from the 16.04.2 ISO, as this version will only be supported for 9 months, versus the 5 year support of 16.04.1.

During the installation, I instruct the installer to download and install updates. Once the OS boots, a lsb_release will identify it as 16.04.1 LTS. When I do apt-get update and apt-get upgrade, lsb_release will now display 16.04.2.

How can I make sure that the OS is as up to date as possible without moving to 16.04.2?

---

### Post by howefield on 2017-06-21
Your installation of 16.04.1 with normal updates will become 16.04.2, 16.04.3, 16.04.4 and 16.04.5 in turn but will still be on the original kernel and graphics stack from 16.04.1 and be supported for the full 5 years.

Installing from the 16.04.2 iso will mean that your kernel stack and graphics stack will be automatically upgraded through 16.04.3, 16.04.4 and 16.04.5 and likewise be supported for 5 years.

In other words installing from either medium will give you the 5 years support, the only difference will be the kernel and graphics stack that you are on.

---

### Post by tatonqek on 2017-06-21
Will these updates take place automatically (with default settings), or is user interaction needed?

I've had issues in the past where we installed with an interim version, time passed, and the attempt to update failed as the repositories were shifted to the archive.

My understanding is that only 16.04, 16.04.1, and 16.04.* (the last release) are the only releases that will be fully supported by security updates throughout the entire 5 year period. If 16.04.1 is "working", I shouldn't need to upgrade unless there is a new feature being added that I need.

---

### Post by deadflowr on 2017-06-21
16.04, 16.04.1, 16.04.2, 16.04.3, 16.04.4, and 16.04.5 are all 16.04 and will all be supported until April 2021.
Keep updating it as you would and it'll be updated as it should be.

The difference between all the point release version are the hardware stack in use. And that depends on the installer used.
If installed from the 16.04 and 16.04.1 installer it will only use the original hardware stack, unless you opt in to use the upgraded hardware stack manually.
So that version will never upgrade the stack.

Installing from the 16.04.2 (and 3,4 5) installer will get newer hardware stacks automatically rolled into them when they are released for the point releases.

Example: if you installed 16.04.1, you will always get the 4.4.0-XX kernel until April 2021.

However if you installed 16.04.2 you will start with the 4.8.0-XX kernel, but when the 16.04.3 point release rolls out (it comes out in Late July/August, typically) you will automatically get moved up to the 4.10.-0-XX kernel without any user intervention (or at least that is the current understanding, 16.04.3 will be the first release to implement this behavior)


Anyway, sidenote: everyone who is running the mostest up-to-date system will be running 16.04.2 according to lsb_release. Regardless of which installation media they used to install Ubuntu 16.04 with.

16.04.2(3,4,5 as well) are more than indicators of hardware stacks as they are also indicators of fully updated software that are inline with the software that came out at time for the point release.
Point releases contain a lot of updates for bugs that have been reported since the last point release, mostly those updates that were accumulated over the last three/six months.

Hope that makes sense.

---

### Post by howefield on 2017-06-21
> **tatonqek said:**
> Will these updates take place automatically (with default settings), or is user interaction needed?

What updates, accepting updates as they are notified to you with default settings will take 16.04.1 through the interim releases automatically but not install the subsequent HWE stacks (kernel/graphics). So it would not be a concern to see 16.04.2 even though you are still on the 16.04.1 HWE.

> I've had issues in the past where we installed with an interim version, time passed, and the attempt to update failed as the repositories were shifted to the archive.

Interim releases are supported for 9 months, this doesn't apply to the releases that you mention in the OP, ie the 16.04 series.

> My understanding is that only 16.04, 16.04.1, and 16.04.* (the last release) are the only releases that will be fully supported by security updates throughout the entire 5 year period. If 16.04.1 is "working", I shouldn't need to upgrade unless there is a new feature being added that I need.

Have a read here : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for information on the new rolling HWE model.

---

### Post by tatonqek on 2017-06-21
Thank you for all the information provided so far.

So then what does the LSB_Release actually indicate?

It indicates 16.04.2. but the kernel version from uname is 4.4.0-31 (the 16.04.1 kernel). Is the support tied to the kernel? So is it 16.04.1 or 16.04.2?

If I installed from 16.04.2, the Kernel would be 4.8. If I didn't update to 16.04.3 by August 2017, that kernel would no longer be supported? I would have to update to 16.04.3 to get the next Kernel version?

Alternatively, the 4.4 Kernel would still be supported through April 2021. Wouldn't it make more sense to stay with the 16.04.1 release and not worry about having to upgrade with each new version?

I apologize for all the questions, but this is all very confusing. It's not like Windows where you just enable automatic updates and hope Microsoft know whats best. :p

---

### Post by howefield on 2017-06-21
> **tatonqek said:**
> It indicates 16.04.2. but the kernel version from uname is 4.4.0-31 (the 16.04.1 kernel). Is the support tied to the kernel? So is it 16.04.1 or 16.04.2?

16.04.1 with all normal updates is now 16.04.2.

Basically it means that whichever point release you install 16.04 from you will still go through the various point releases till the last one 16.04.5. The only difference will be which HWE stack that you are on. The HardWare Enablement stacks only benefit newer hardware in the main, so if 16.04.1 works for you then you do not need to worry, just stay on it, but you will still see your installation as 16.04.2 ect.

> If I installed from 16.04.2, the Kernel would be 4.8. If I didn't update to 16.04.3 by August 2017, that kernel would no longer be supported? I would have to update to 16.04.3 to get the next Kernel version?

Starting with 16.04.2 the kernel included with 16.04.2 would be automatically upgraded when the next HWE was released along with 16.04.3.

> Alternatively, the 4.4 Kernel would still be supported through April 2021. Wouldn't it make more sense to stay with the 16.04.1 release and not worry about having to upgrade with each new version?

It's purely your choice, unlike previous LTS releases the point releases .2 through .5 are automatically upgraded so you won't have to worry about ending up on an unsupported kernel.

> I apologize for all the questions, but this is all very confusing. It's not like Windows where you just enable automatic updates and hope Microsoft know whats best. :p

No apologies needed, this is a forum built for asking questions.

---

