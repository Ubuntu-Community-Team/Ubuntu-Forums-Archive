---
title: "BTRFS grinds to halt"
date: 2016-02-27
forum: General Help
---

### Post by stone circle on 2016-02-27
[FONT=arial]Hi,

I have a BTRFS system serving virtual disks to a hypervisor, and there is a process: btrfs-transacti that regularly utilizes 100% CPU.  While it sits at 100%, my VMs are frozen and unusable.  Does anyone know of a way of checking what exactly btrfs-transacti is doing?  

All the virtual disk files have the nodatacow btrfs attribute enabled.  According to the [btrfs wiki]("https://btrfs.wiki.kernel.org/index.php/Gotchas") this should prevent btrfs-transacti [COLOR=#000000]taking up a lot of CPU time.

Any suggestions?
[/COLOR][/FONT]

---

### Post by TheFu on 2016-02-27
There was/is a bug with using btrfs on hypervisors. [http://www.linux-kvm.org/page/Tuning_KVM](http://www.linux-kvm.org/page/Tuning_KVM)> 
Don't use the linux filesystem btrfs on the host for the image files. It will result in low IO performance. The kvm guest may even freeze when high IO traffic is done on the guest. 
Don't know when/if it was fixed.  Decided to avoid btrfs for now.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1513076](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1513076) says the bug is back in the 4.2.x kernels.

---

### Post by X-RED_Tech on 2016-02-28
> **TheFu said:**
>  Decided to avoid btrfs for now.

Me too.
There are other problems/bugs that affect normal installations as well. It needs a lot of ironing until it becomes a viable alternative to the usual EXts.

---

### Post by stone circle on 2016-03-26
If I want the benefits of BTRFS snapshots (easy backup, etc), perhaps I should minimise the reliance on large image files.  If I continue to use image files for each VM's OS, but create NFS shares on BTRFS system (a NAS) which are mounted within each VM for the data, home, temp & possibly apps directories, then BTRFS will less likely lock-up due to fragmentation or whatever is causing btrfs-transacti to be 100% utilised.  This way BTRFS will generally deal with lots of small files, which it is better at, than a few large ones.  Can anyone validate this approach?

---

### Post by TheFu on 2016-03-26
LVM + snapshots, then I use rdiff-backup for backups.  

BTRFS will be amazing, when it is ready for all use scenarios.

Have you looked at QCOW2 snapshots? Just an option, though I didn't like it for our needs.

---

