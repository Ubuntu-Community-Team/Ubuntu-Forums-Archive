---
title: "Can[t access external USB HD"
date: 2008-03-17
forum: General Help
---

### Post by SeattleUser on 2008-03-17
I have accessed it previously and backed up my account to it. That was a few months ago. Now when I plug it in it doesn't get mounted and there is no relevant link in /etc/fstab. The HD is formatted with the ext3 filesystem. It doesn't show up in the lsusb report.

Dmesg reports this when I plug it in:
[ 1956.775736] usb 5-2: new high speed USB device using ehci_hcd and address 5
[ 1956.907962] usb 5-2: configuration #1 chosen from 1 choice

What can I do?

It also has firewire ports and I have used firewire for my camcorder. Is there any way I can force a mount? Could it be misbehaving because the file system is corrupted?

---

### Post by Rocket2DMn on 2008-03-18
Can you please post the output of
```
sudo fdisk -l
```
while the drive is plugged in.  Use USB for now, it is easier to setup I think.

---

