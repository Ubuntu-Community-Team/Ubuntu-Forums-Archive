---
title: "What is grub's &quot;recordfail&quot; and how to investigate?"
date: 2019-02-08
forum: General Help
---

### Post by clepsdyrae on 2019-02-08
I'm running Lubuntu 18.04.1 on a laptop. I configure it to boot directly to the default linux install (there are no other installs on the laptop) with no grub screen. It's been fine for months, but a recent package update caused the grub screen to start appearing again, every time with a 30s countdown. Grub version is 2.02.

This is apparently due to the "recordfail" condition being true, which changes the timeout to 30s (via /boot/grub/grub.cfg). Setting GRUB_RECORDFAIL_TIMEOUT=5 for example makes it boot as expected (5 second delay in that case.)

My understanding is that "recordfail" means the computer didn't shut down cleanly? Is that correct?

I don't see any obvious errors in the logs -- how can I investigate why "recordfail" is being set?

Thanks!

---

### Post by Dennis N on 2019-02-08
> This is apparently due to the "recordfail" condition being true, which changes the timeout to 30s (via /boot/grub/grub.cfg). Setting GRUB_RECORDFAIL_TIMEOUT=5 for example makes it boot as expected (5 second delay in that case.)

A question for you: If you add this setting, doesn't the grub menu still appear for (up to) 5 seconds?

I saw the same problem this morning, but haven't yet done anything about it.

---

### Post by dmnur on 2019-02-08
Do you use LVM or LUKS encryption? Maybe btrfs or ZFS? Also you probably have EFI.

See here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722)
Seems to be a regression in **grub-common 2.02-2ubuntu8.10**.

---

### Post by Dennis N on 2019-02-08
> **dmnur said:**
> Do you use LVM or LUKS encryption? Maybe btrfs or ZFS? Also you probably have EFI.

See here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722)
Seems to be a regression in **grub-common 2.02-2ubuntu8.10**.

This is UEFI and LVM. There is only Ubuntu 18.04 installed on this machine, and up to now, no grub menu appeared. My take on this is that a grub menu is now going to appear in all cases with UEFI (but not BIOS) just to be sure users can get a menu when needed.    

Comments:

There is no setting GRUB_RECORDFAIL_TIMEOUT= in my /etc/default/grub. Do you have that, or did you add it? I get the 30 sec timeout without it.

---

### Post by dmnur on 2019-02-09
Looks like it's fixed now: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1814403](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1814403)
Upgrade and celebrate. :)

---

### Post by clepsdyrae on 2019-02-18
Thanks all -- I subscribed to the thread for email updates but never got them for some reason (?). I just came back to say that the problem resolved itself with recent package updates, as dmnur suggested it would. Thanks for the responses!

---

### Post by cthart on 2019-04-02
I'm running 18.10, with all updates and am also getting this problem. I haven't edited my grub configuration, but I'm getting a 30 second delay on every boot, regardless of how I shut down my machine. Booting using UEFI. Root partition is on LVM.
I did experience some lock-ups with my AMD Ryzen 5 1500X CPU, but I changed the power settings in the BIOS to work around this and since then the computer has been rock-stable.
Is there still some failure recorded that I need to clear somehow? How?
I just added proposed to APT and installed all the updates from there too, no change.

---

### Post by clepsdyrae on 2019-04-02
I'm afraid I can't help at all, but I would try adding the "GRUB_RECORDFAIL_TIMEOUT=5" to /etc/default/grub, updating the grub config, and rebooting, just for the sake of confirming that it's the recordfail issue causing the problem? (Maybe you already did this.)

When I updated from the repo I did not to clear any old state, it just worked after that.

What distro are you using?

---

### Post by Dennis N on 2019-04-02
> Is there still some failure recorded that I need to clear somehow? How?
There is no actual failure. It's a deliberately faked failure set by a script to force grub menu to appear. I think this is set only on systems with one OS, UEFI and LVM. All three must be satisfied* to trigger this.

The reasoning was that otherwise you can't get the grub menu to appear on such a system if you needed it for an advanced option (like recovery mode). Just press enter to cancel the 30 sec time delay. Boot will then continue.

*based on some experiments done in a VM done a few months ago.

---

