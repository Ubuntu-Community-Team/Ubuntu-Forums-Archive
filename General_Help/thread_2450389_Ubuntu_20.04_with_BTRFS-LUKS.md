---
title: "Ubuntu 20.04 with BTRFS-LUKS"
date: 2020-09-12
forum: General Help
---

### Post by XBMC old School on 2020-09-12
I want to fresh release install of 20.04 and utilizes btrfs-luks on / & /home.

However, i want to mount /home on a separate partition so that moving forward i can release/distro hop without loosing my /home folder. 

I looked at a few tuts and found this one:
[(https://youtu.be/yRSElRlp7TQ?t=617) Looking at his partition table.  Questions: 1. Do i parallel his installation but with an /dev/sda4 & /dev/mapper/crypt_home (400gb /home & 100GB /)?  2. After this is done, with all the partitions encrypted w/ keyfiles. Will shrinking the root partition and doing a secondary install with next the distro/release be painful to dual boot or have both options in grub?  Thanks"]https://youtu.be/yRSElRlp7TQ?t=617]("http://I want to fresh release install of 20.04 and utilizes btrfs-luks on / & /home.  However, i want to mount /home on a separate partition so that moving forward i can release/distro hop without loosing my /home folder.   I looked at a few tuts and found this one: [https://youtu.be/yRSElRlp7TQ?t=617)
Looking at his partition table.

Questions:
1. Do i parallel his installation but with an /dev/sda4 & /dev/mapper/crypt_home (400gb /home & 100GB /)?

2. After this is done, with all the partitions encrypted w/ keyfiles. Will shrinking the root partition and doing a secondary install with next the distro/release be painful to dual boot or have both options in grub?

Thanks

---

