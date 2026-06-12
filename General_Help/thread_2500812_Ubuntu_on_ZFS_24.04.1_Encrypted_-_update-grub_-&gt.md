---
title: "Ubuntu on ZFS 24.04.1 Encrypted - update-grub -&gt; failure at boot until zpool export"
date: 2024-09-12
forum: General Help
---

### Post by sharptiger on 2024-09-12
I have a clean install of Ubuntu on ZFS 24.04.1 with an encrypted disk, using the GUI installer and not customizing the disk setup.

Installation went fine, and I was able to boot regularly.

Then I decided to compile a new kernel (6.10) and install it - but note that in the expanation below I am working with the originally installed 6.8.0-41-generic kernel.

* I run update-grub.
* I reboot.

Choosing the originally shipped kernel:
* Boot fails with "error: sparse file not allowed"
The internet says that this means I should be turning off `recordfail`, but that looks turned off already.

Choosing recovery mode:
* Recovery mode also fails to boot, unable to decrypt when given the correct password.
* `zpool export bpool` and `zpool export rpool`, then booting in recovery mode works.

At this point I still do not have the non-recovery mode booting. Hopefully I will figure that out soon. I would be grateful for ideas.

I don't understand what is going on here or how to fix it at this point. I am a ZFS beginner but not for long, unfortunately.

---

### Post by 1fallen on 2024-09-12
It's best not to tamper with Kernels on a ZFS system, one good way to break it as you now have seen.

If you want stability stay within what the kernel-team provides for us.

As a tester I do play with newer kernels to see how things are going for ZFS, but not recommended for newer users

BTW My system:
```
inxi -Fbx|grep fs
  Host: Legion-5-15ACH6-zfs Kernel: 6.10.0-15-generic arch: x86_64 bits: 64
  IF-ID-2: surfshark_ipv6 state: unknown speed: N/A duplex: N/A
  IF-ID-3: surfshark_wg state: unknown speed: N/A duplex: N/A mac: N/A
  Device-1: bpool type: zfs status: ONLINE level: linear raw: size: 1.88 GiB
    free: 1.68 GiB zfs-fs: size: 1.75 GiB free: 1.56 GiB
  Device-2: rpool type: zfs status: ONLINE level: linear raw: size: 456 GiB
    free: 418 GiB zfs-fs: size: 441.88 GiB free: 403.56 GiB
  ID-1: / size: 413.85 GiB used: 10.29 GiB (2.5%) fs: zfs
  ID-2: /boot size: 1.75 GiB used: 192.9 MiB (10.8%) fs: zfs
  ID-3: /boot/efi size: 1.05 GiB used: 6.1 MiB (0.6%) fs: vfat
  ID-4: /home size: 427.35 GiB used: 23.79 GiB (5.6%) fs: zfs
  ID-5: /var/log size: 403.64 GiB used: 88.8 MiB (0.0%) fs: zfs
```
Kernel in use:
```
apt policy  linux-image-6.10.0-15-generic
linux-image-6.10.0-15-generic:
  Installed: 6.10.0-15.15
  Candidate: 6.10.0-15.15
  Version table:
 *** 6.10.0-15.15 100
        100 /var/lib/dpkg/status



```
Note I did not compile it.

6.11 still needs a touch here and there but it is doable:
```
uname -a
Linux Legion-5-15ACH6-zfs 6.11.0-1002-lowlatency #2-Ubuntu SMP PREEMPT_DYNAMIC Tue Sep 10 08:06:06 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux


```
I really need to stress 6.11 is in "proposed" and again not recommended.
```
apt policy linux-image-6.11.0-1002-lowlatency
linux-image-6.11.0-1002-lowlatency:
  Installed: 6.11.0-1002.2
  Candidate: 6.11.0-1002.2
  Version table:
 *** 6.11.0-1002.2 100
        _**100 http://us.archive.ubuntu.com/ubuntu oracular-proposed/main amd64 Packages**_
        100 /var/lib/dpkg/status

```

---

### Post by sharptiger on 2024-09-12
Does not address the question.

---

### Post by 1fallen on 2024-09-12
It dose address the question, Don't stray from the Original kernel. Especially when LUKS is involved.

Any who will you show this please:
```
sudo update-initramfs -c -k all
```

I take it your a Stack Exchange user....;)

---

