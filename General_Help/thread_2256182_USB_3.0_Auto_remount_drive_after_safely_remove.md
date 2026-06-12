---
title: "USB 3.0 Auto remount drive after safely remove"
date: 2014-12-10
forum: General Help
---

### Post by ubuserone on 2014-12-10
USB 3.0 Auto remount drive after safely remove my external 2.5 inch hard disk.
Using ubuntu 14.04 at 3.13.0-39-generic .

If I switch to USB 2.0 , it doesn't auto remount.
Which log do I need to provide for support ?

---

### Post by mc4man on 2014-12-10
Does the same nonsense here, haven't gotten to the bottom of yet. (may file a bug if it happens in vivid which I need to re-install.

The only current workaround here is to either boot up with the drive connected or connect the drive > log out/in
Then the safely remove option disappears & only option is to Unmount which does work 
(- whether not having an eject option with Unmount could also be an issue. Whether Unmount is totally safe not sure, seen no issues yet.

The drive is partitioned to ext4 here.

---

### Post by ubuserone on 2014-12-10
> **mc4man said:**
> Does the same nonsense here, haven't gotten to the bottom of yet. (may file a bug if it happens in vivid which I need to re-install.

The only current workaround here is to either boot up with the drive connected or connect the drive > log out/in
Then the safely remove option disappears & only option is to Unmount which does work 
(- whether not having an eject option with Unmount could also be an issue. Whether Unmount is totally safe not sure, seen no issues yet.

The drive is partitioned to ext4 here.
Unmount is not totally safe,  it doesn't power down the drive and it increase the power off retrack counts by 1 at SMART everytime I just unplug the cable after unmount.

I remember a lot of user facing it?

---

### Post by mc4man on 2014-12-12
The remounting is just from the default file manager settings but the complete inability to power down a usb 3 hdd (no external power type) connected to a usb 3 port  is a bit disturbing. 
(- I don't think I'll use this device on linux anymore until you can
Tested in 15.04,  same deal though even more issues - takes about 30 sec to become available after connecting vs. 1 sec in 14.04
filed bug on linux though maybe not the kernel's issue & may not go anywhere (or is a dupe
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1401980](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1401980)

---

### Post by mc4man on 2014-12-13
Best  workaround here (other than never detaching) *may* be to go to suspend. That does power off the device. 
(- whether properly don't know, trust level regarding this in linux is low.

---

### Post by ubuserone on 2014-12-16
It's more like a bug to me since usb 2.0 port work perfect , not on usb 3.0 though.

---

