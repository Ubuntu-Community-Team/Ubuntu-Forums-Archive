---
title: "About upgrade 20.04 to 22.04"
date: 2022-06-07
forum: General Help
---

### Post by satimis on 2022-06-07
Hi all,

Please advise what will be the reliable way upgrading Ubuntu 20.04 desktop to 22.04 desktop.  Ubuntu 20.04 is the host of KVM.  KVM is running on it with about 12 guests installed.  Should there is any problem, KVM has to be reinstalled.

Thanks in advance

Regards

---

### Post by Dennis N on 2022-06-07
I plan to do the same upgrade, but it's not time yet for an in-place upgrade. Wait until the first point release or later, at which time Software Updater will offer the upgrade most reliably. 

I did the 1804 to 2004 upgrade on the same system about a year ago and there was no problem with the guest VMs. They just worked.

You could do a new install now and replace 2004, but then you face hours of work setting up the system to the same functionality. VMs can be imported if they are using qcow2 storage.

---

### Post by satimis on 2022-06-07
> **Dennis N said:**
> I plan to do the same upgrade, but it's not time yet for an in-place upgrade. Wait until the first point release or later, at which time Software Updater will offer the upgrade most reliably. 

I did the 1804 to 2004 upgrade on the same system about a year ago and there was no problem with the guest VMs. They just worked.

You could do a new install now and replace 2004, but then you face hours of work setting up the system to the same functionality. VMs can be imported if they are using qcow2 storage.
Thanks for your advice.

I have Ubuntu 22.04 installed and running on VM of VirtualBox on another SSD of this PC.

I have GIMP running here.  Because some of the filter plugin of GIMP unable to run on Ubuntu 20.04.  That is the only reason I need to upgrade to Ubuntu 22.04

Regards

---

