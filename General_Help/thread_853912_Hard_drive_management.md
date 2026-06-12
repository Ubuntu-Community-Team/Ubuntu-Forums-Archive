---
title: "Hard drive management"
date: 2008-07-09
forum: General Help
---

### Post by swordphsh on 2008-07-09
I have Ubuntu Server running on an old computer with a few 40 gig drives in it and am running TorrentFlux on it. I'm looking for a way to automatically distribute files evenly between the 3 partitions.

Not anything like striping, but just having one mount point, but the software would distribute files between the 3 drives so I dont have to keep track of how much free space I have on each drive.

I dont want to set up a Raid 0 though because they are somewhat old drives and I'd rather just lose 40 gigs of data if one dies, rather than 120 gigs.

Thanks in advance for any input.

---

### Post by logos34 on 2008-07-09
I believe you want to look into LVM.

This might help or at least get you started:
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)
[http://en.wikipedia.org/wiki/Logical_volume_management](http://en.wikipedia.org/wiki/Logical_volume_management)

---

### Post by swordphsh on 2008-07-10
> **logos34 said:**
> I believe you want to look into LVM.

This might help or at least get you started:
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)
[http://en.wikipedia.org/wiki/Logical_volume_management](http://en.wikipedia.org/wiki/Logical_volume_management)

Thanks, that looks like exactly what I'm looking for.

I have a few questions though about it because the guide is a bit confusing. I get that I need to create a blank partition and format it as Linux LVM, but then after that, how would I extend it into other partitions? Do they need to blank and formatted the same or can I add existing partitions that already have data on them?

The way I have the system set up is 3 hard drives, all 40 gigs, one drive has my linux system installed, one has windows (ntfs), and a third is filled with data such as movies. My plan is to make a logical volume out of the third drive, and half of each of the other two drives.

---

