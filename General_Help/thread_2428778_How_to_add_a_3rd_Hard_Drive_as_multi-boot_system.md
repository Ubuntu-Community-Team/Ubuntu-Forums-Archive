---
title: "How to add a 3rd Hard Drive as multi-boot system"
date: 2019-10-09
forum: General Help
---

### Post by satimis on 2019-10-09
Hi all,

Configuration:-
AMD - 8 cores
RAM - 32G
SSD-SanDisk 250G - Ubuntu 18.04 (for graphics and video editing)
SSD-Samsung 2TB - Ubuntu 16.04 (Host for VirtualBox VMs)
WD-4TB for storage
WD-2TB for storage

BIOS settings
1st boot = SSD-SanDisk 250G
2nd boot = SSD-Samsung EVO 2TB

At booting```

Ubuntu
Advanced options fo Ubuntu
Ubuntu 18.04.3 LTS (18.04 (on /dev/sde2)
*advanced options for Ubuntu 18.04.3 LTS (18.04) (on /dev/sde2)
Ubuntu 16.04.6 LTS (16.04) (on /dev/mapper/ubuntu--vg-root)
Advanced options for Ubuntu 16.04.6 (16.04) (on /dev/mapper/ubuntu--vg-root)
System Setup

```

1) selecting "Ubuntu" boots "SSD-SanDisk 250G"
2) selecting 'Ubuntu 16.04.6 LTS (16.04) (on /dev/mapper/ubuntu--vg-root)" boots "SSD-Samsung EVO 2TB"

Now I'm prepared adding a 3rd SSD-Samsung EV0 500G solely for hosting KVM.  If it is possible please advise how.

Thanks in advance.

Regards
satimis

---

### Post by TheFu on 2019-10-10
Seems like a trick question.  Just install Ubuntu onto the 3rd disk and update grub on the disk where it is today.
Why split the OSes to different physical drives?  I wouldn't.
Why have virtualbox and KVM?  I wouldn't.
Why have a video editing specific install?  I wouldn't.

All of those things can easily be used under a single KVM install.  Just don't startup any VMs when you want to do video editing.  With nested virtualization, you can run virtualbox inside a VM under KVM, or just tell KVM to run the VDMK VMs itself.

Seems like 50G of wasted storage when it isn't needed, plus you have to backup that stuff, so that's 2x more wasted storage.  I must be missing something, right?

---

### Post by satimis on 2019-10-10
> **TheFu said:**
> Seems like a trick question.  Just install Ubuntu onto the 3rd disk and update grub on the disk where it is today.
Why split the OSes to different physical drives?  I wouldn't.
Why have virtualbox and KVM?  I wouldn't.
Why have a video editing specific install?  I wouldn't.

All of those things can easily be used under a single KVM install.  Just don't startup any VMs when you want to do video editing.  With nested virtualization, you can run virtualbox inside a VM under KVM, or just tell KVM to run the VDMK VMs itself.

Seems like 50G of wasted storage when it isn't needed, plus you have to backup that stuff, so that's 2x more wasted storage.  I must be missing something, right?
Hi,

Thanks for your advice.

I have been running VirtualBox VMs for graphic and video editing for long time.  But later I found it would be faster if doing them on native drive.  For such a reason I installed dual-boot PC, one drive solely for hosting VirtualBox VMs and another for graphic and video editing.

I have 2 PCs;

PC1-Dual Boot
===========
Drive1 - SSD 2TB (before SSD 1TB, just replacing it with a new SSD 2TB about 3~4 months ago)
OS - Ubuntu 16.04 for running VirtualBox
Drive2 - SSD 250G
OS - Ubuntu 16.04 for running KVM
Drive3 WD2TB and Drive4 WD1.5TB solely for storage (just replaced with a WD4TB new drive).
This is a powerful PC running AMD 8-core CPU with 32G RAM installed.

I just purchased a new Samsung SSD 500G to be added to this PC solely for graphic and video editing

PC2-Dual Boot
===========
Drive1 - SSD 1TB
OS - Ubuntu 16.04 for running VirtualBox
Drive2 - SSD 250G
OS - Ubuntu 16.04 solely for graphic and video editing
Drive3 WD2TB and Drive4 WD1TB solely for storage.
This PC is running AMD 8-core CPU with 8G RAM installed.

I'm now going to upgrade all OS to Ubuntu 18.04.  That is my present situation.

Regards
satimis

---

