---
title: "Upgrade to HWE-Raring of VBox guest causes guest additions to fail."
date: 2013-09-18
forum: General Help
---

### Post by bamm on 2013-09-18
Hello,

I am running Ubuntu Precise 12.04 LTS as Virtualbox Guest. I upgraded the guest by installing Hardware Enablement Stack for Raring. After that, Guest Additions no longer works properly. In particular, the package virtualbox-guest-x11 gets uninstalled and fails to reinstall. Same with other packages whose names begin with virtualbox-guest-*. Because of this, I am stuck with a very low resolution on the guest.

Is there some way I can get this working the way it did before upgrading to hardware enablement? I appreciate any answers and suggestions.

Regards,
Bamm

---

### Post by QIII on 2013-09-18
Hello!

May I ask what you were trying to accomplish with the Hardware Enablement Stack, given that the hardware abstraction layer in VBox is fixed and known?  The stacks are not really intended for virtual or cloud environments.

---

### Post by bamm on 2013-09-18
I am working in a VM so as not to tinker so much with my production system. This is for a project to roll a distribution for internal use. The guest OS will then be saved as a LiveDVD using Remastersys. While the guest additions are not required, it will surely improve the experience running the LiveDVD.

We already have a previous version of this based on 12.04, and it is stable and works well for us. Since we are working on a new release (it's been almost a year since our previous release) I figured I could support more hardware by upgrading the kernel to HWE.

---

### Post by bamm on 2013-09-18
I found a similar concern about VirtualBox not working with HWE but this is about running VBox in Ubuntu with HWE installed, not HWE in a VirtualBox guest.
[http://askubuntu.com/questions/342370/virtualbox-stopped-working-in-12-04-lts-after-i-upgraded-kernel-using-hardware-e](http://askubuntu.com/questions/342370/virtualbox-stopped-working-in-12-04-lts-after-i-upgraded-kernel-using-hardware-e)

However I found the solution interesting, particularly the patch to VBox to make it work. Is there a similar patch for virtualbox-guest-dkms and virtualbox-guest-x11? The problem in the link above is virtualbox-dkms, not virtualbox-guest-dkms, but perhaps there could be a similar solution?

---

### Post by bamm on 2013-09-22
> **QIII said:**
> May I ask what you were trying to accomplish with the Hardware Enablement Stack.

Hi QIII, I hope my clarification has helped. Would you have any suggestions I can try? Thanks.

---

### Post by bamm on 2013-10-06
any answers on how to install the guest additions on precise with hardware enablement stack raring?

---

