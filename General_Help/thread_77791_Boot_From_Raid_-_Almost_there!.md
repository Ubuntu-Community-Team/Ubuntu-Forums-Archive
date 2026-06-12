---
title: "Boot From Raid - Almost there!"
date: 2005-10-17
forum: General Help
---

### Post by theminor on 2005-10-17
I found [this]("http://ubuntuforums.org/showthread.php?t=67498") post about someone who has successfully installed ubuntu onto a second partition of his sil RAID array, which is fake raid.  I have almost the exact same setup, except I am using NVRAID.  Both of these types are supported through the dmraid utility.  A [How-To]("https://wiki.ubuntu.com/FakeRaidHowto") is now up at the ubuntu wiki, and I have been following it trying to get my system to boot with dmraid.  I have been able to install ubuntu on the new partition, now the only thing I have to do is set up lilo properly, which is the tricky part.  I've tried and tried to get my lilo.conf set correctly, but I'm still having problems.

Has any one else successfully gotten this to work?  My latest question is this: after you chroot to the /target folder, how to you run lilo from there?  Lilo complains that it cannot find the /dev/mapper/nvraid device (because this is not there, since you chroot-ed to the /target directory; rather, the /dev/mapper/nvraid device is in the origional root). With the new chroot, the actual place lilo is looking for is really /target/dev/mapper/nvraid_.  Anyone have any further insight or more specific steps to get lilo configured?

Thanks!

---

