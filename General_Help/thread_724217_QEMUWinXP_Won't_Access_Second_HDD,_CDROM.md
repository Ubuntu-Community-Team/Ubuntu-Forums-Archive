---
title: "QEMU/WinXP Won't Access Second HDD, CDROM"
date: 2008-03-14
forum: General Help
---

### Post by gus_zernial on 2008-03-14
I'm running QEMU/WinXP guest on Kubuntu 7.10 host. Windows system disk is on ~/windows.img, which happens to be on Linux software RAID (works fine). I have a separate disk /dev/sdc which I'd like to access from the WinXP guest, and I have a CDROM /dev/scd0 which I'd also like to access from the WinXP guest. Here's my QEMU startup command and options ...

sudo qemu -hda -hdb /dev/sdc -cdrom /dev/scd0 -soundhw all ~/windows.img -boot c -net nic,model=rtl8139 -net tap, ifname=tap0

Networking and sound are working, but I can't access /dev/sdc or /dev/scd0 from the WinXP quest. Appreciate correction of my startup command, or other information on how to do this.

---

