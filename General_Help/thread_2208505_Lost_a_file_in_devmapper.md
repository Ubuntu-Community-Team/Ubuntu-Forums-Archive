---
title: "Lost a file in /dev/mapper"
date: 2014-02-28
forum: General Help
---

### Post by JebusWankel on 2014-02-28
My VM host machine has LVM. When I set up one of my guest VMs, instead of putting it into the logical volume I created for it in /dev/mapper/host--name--vg-vmname, I put a typo in the name of the logical volume, so it created a raw file for it called /dev/mapper/host-name--vg-vmname. So the VM ran fine but when the host machine was accidentally rebooted, that file was lost. How do I restore this raw vm image file? Was it just living in memory? Can I recover it with some sort of undelete utility? Could I get it from swap?

---

