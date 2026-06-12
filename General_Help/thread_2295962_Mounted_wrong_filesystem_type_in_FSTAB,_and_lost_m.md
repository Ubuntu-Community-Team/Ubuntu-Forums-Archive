---
title: "Mounted wrong filesystem type in FSTAB, and lost my data after corrected mount"
date: 2015-09-22
forum: General Help
---

### Post by elliott6 on 2015-09-22
Running a mythbuntu 12.04 LTS server with hardware raid storage (but question is not specific to mythbuntu or raid, so I thought I would post here).

I was moving and adding additional storage, and mindless me changed the xfs system type to ext4 in fstab because I was mounting an additional array (with ext4) and made the wrong change. As a result, the partition did not mount properly. Got a bad superblock warning after I corrected the mount parameters, and running a xfsrepair check yielded me the proper partition structure, etc., but my data is no longer showing. Might be because of a conflicting mount point as well (since corrected).

Is there anything anyone here could recommend for me to retrieve my data (it's around 5TB)? I have the majority backed up, but am missing a few hundred pictures of the little ones (which would be a problem, especially with the misses - small time gap I didn't save elsewhere apparently - well, I did, except I was moving that storage that got me to my mixup), and some recordings (I'm less concerned about) and videos.

There is only 2GB currently showing on the partition of the total 5TB storage, so it obviously hasn't overwritten. But again, the appropriate data isn't evident. What am I missing, and what steps might I be able to take.

Thanks for reading! Sorry, and please ask, if I left anything out.

elliott

---

