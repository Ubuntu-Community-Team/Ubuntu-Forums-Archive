---
title: "Files Partition Read Only?"
date: 2007-06-10
forum: General Help
---

### Post by chantzzzzz on 2007-06-10
I just installed Ubuntu 7.04, and my hard drive is partitioned as such:

10GB Windows XP Pro SP2
10GB Ubuntu 7.04
1GB SWAP
37GB Shared Files

Now I had intended for the 37GB to be used between XP and Ubuntu, but after restoring all of my files from my iPod in XP, Ubuntu can't do anything with them, nor can it make any more additions. It's windows formatted for ntfs, but that shouldn't make a difference I would hope. Any advice on the matter would be appreciated. Thanks!

---

### Post by taurus on 2007-06-10
You need to install ntfs-3g driver before you can write to ntfs filesystem.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

