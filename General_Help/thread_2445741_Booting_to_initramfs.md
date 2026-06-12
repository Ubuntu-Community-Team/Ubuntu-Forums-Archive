---
title: "Booting to initramfs"
date: 2020-06-18
forum: General Help
---

### Post by andre46 on 2020-06-18
I'm running Ubuntu MATE 20.04 VMs installed on XCP-ng. I started having weird issues today with one of my VMs, so I bounced it, and now I can't get it back online. The VM boots directly to GRUB. When I select Ubuntu, it loads the initramfs page with the following errors listed:

```
Initramfs unpacking failed: Decoding failed
vbd vbd-5696: 19 xenbus_dev_probe on device/vbd/5696
piix4_smbus 0000:00:01.3: SMBus Host Controller not enabled!
```

So I found this guide to [blacklist the piix4_smbus]("https://askubuntu.com/questions/691729/piix4-smbus-0000007-3-host-smbus-controller-bus-not-enabled"). When I enter Advanced Options, I have 2 kernels available. When I boot to either of the two Recovery Mode kernels, the screen loads as just complete static. I can see a blinking cursor towards the middle of the screen, but I can't read anything on the screen. I've tried viewing the screen in XCP-ng Center and Xen Orchestra, but static either way. So basically I can only boot to the normal kernels, and I can't appear to get to Recovery.

I had 4 recent snapshots. The oldest one was 2 weeks ago, and I get the same issue when trying to restore from any of the snapshots. I have no idea what caused this and why I can't recover from it. Any help would be greatly appreciated.

---

### Post by andre46 on 2020-06-18
I just realized I could detach the disk from the VM and attach it to another VM to edit the file, or even boot the VM from a live CD. So I booted from a Live CD, but I am unable to mount the OS drive. Not sure where to go from here.

---

### Post by andre46 on 2020-06-19
As I said before, when in the Live CD, I can't mount the OS drive. I can mount the EFI partition only.

```
sudo mount /dev/xvda2 /mnt
mount: /mnt: can't read superblock on /dev/xvda2
```

I can only mount xvda1, which doesn't really help. There isn't anything wrong with the disk, since it's just a virtual disk that exists on the same physical disk that is currently hosting several other VMs.

---

### Post by andre46 on 2020-06-20
I figured it out.


Each of my virtual disks appeared to have plenty of space remaining. However, the physical disk that hosts all of my OS drives was completely full.


I removed some VMs and made some space, and then was able to revert to an existing snapshot and boot. This is now resolved.

---

