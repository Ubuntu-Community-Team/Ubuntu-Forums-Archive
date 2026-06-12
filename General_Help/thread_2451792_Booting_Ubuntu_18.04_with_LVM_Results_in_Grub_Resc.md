---
title: "Booting Ubuntu 18.04 with LVM Results in Grub Rescue Prompt"
date: 2020-10-11
forum: General Help
---

### Post by randomparity on 2020-10-11
I have an Ubuntu 18.04 VM that has suddenly started dropping into the grub rescue command line.  The message is as follows:

error: disk 'lvmid/KddNhA-.../nUNaco-...' not found.
grub rescue> set
cmdpath=(hd0)
prefix=(lvmid/KddHhA-.../nUNaco-...)/boot/grub
root=lvmid/KddNhA-.../nUNaco-...
grub rescue> ls
(hd0) (hd0,msdos1) (lvm/docker--vg-download) (lvm/docker--vg-appdata) (lvm/docker--vg-swap) (lvm/docker--vg-root)

I've tried booting an Ubuntu 18.04 ISO and using the "Rescue mode" option "Reinstall GRUB boot loader" with no effect. 

 When using the "Execute a shell in /dev/docker-vg/root" option I can see my data and I can verify that the LVM UUIDs used by grub are correct (the first is the volume group and the second is the logical volume for root).  The LVM volume group "docker-vg" consists of two drives (512GB, partitioned with MBR, and 4TB, partitioned with GPT).

The "Troubleshooting" section of [http://www.gnu.org/software/grub/manual/grub/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub/grub.html#Troubleshooting) is pretty thin, and a Google search doesn't show many examples with LVM involved.  What other steps are available to me to fix the issue?

Dave

---

