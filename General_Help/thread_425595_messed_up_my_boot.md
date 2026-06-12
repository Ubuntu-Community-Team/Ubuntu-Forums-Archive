---
title: "messed up my boot"
date: 2007-04-27
forum: General Help
---

### Post by Amilius on 2007-04-27
I just messed up my 'puter.  I had Kubuntu installed on my computer together with Windows XP, I wanted to upgrade my kubuntu Dapper to Edgy, so I googled how to do it, changed the sources.list to edgy and used the dist-upgrade... total failure... it started alright, and then it just stopped downloading the packages and didn't let me upgrade anything... all packages that I tried to upgrade thru GUI seemed to break... so I restart my computer and Kubuntu didn't want to load up.  So here's when I mess things up even more, thru Windows XP  I deleted the partition that had Kubuntu installed and now it seems that the GRUB wants to load but a message saying Error 17 appears and it stops right there... now I can't load kubuntu nor Windows XP.  Is there anyway to eliminate GRUB so I can directly boot to Windows? if I Install Ubuntu using live CD, will it overwrite that grub if I use the partition where the last kubuntu installation was?

---

### Post by disturbedite on 2007-04-27
i'm not sure about this, all i know from experience is don't install a linux distro and then install windows; it will overwrite the master boot record!  do it the other way around.

---

### Post by Amilius on 2007-04-27
well, you see, Windows is still there, the problem is that I can't boot to it.  the disk is already partitioned, so I don't think it'll overwrite windows... but how can I get into windows?

---

### Post by GuitarRocker2562 on 2007-04-27
just re-install kubuntu, it will re-install GRUB, gub can't load because part of GRUB was on your kubuntu partition, re-installing will re-install grub too.

---

### Post by disturbedite on 2007-04-27
> **GuitarRocker2562 said:**
> just re-install kubuntu, it will re-install GRUB, gub can't load because part of GRUB was on your kubuntu partition, re-installing will re-install grub too.
you could do that, but i'd reserve that course of action as a last resort.  but you can reinstall grub by itself without having to reinstall *buntu.  i don't know how to do that tho, so i'd look around.

---

