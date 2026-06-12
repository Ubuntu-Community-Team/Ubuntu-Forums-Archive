---
title: "Emergency: I just formatted /boot on LUKS system -- but still logged in"
date: 2019-06-15
forum: General Help
---

### Post by mnealbarrett on 2019-06-15
I just accidentally formatted the /boot partition on a system set up with LUKS.  Since it uses LUKS, if I log out, I will not be able to go the "live CD" route to reinstall or recover the /boot partition.  I am still logged in, though.

/boot is on the "partition" /dev/mapper/isw_bddchfhcc_Volume0p1.  

I tried a couple of things.  I tried sudo grub-install /dev/mapper/isw_bddchfhcc_Volume0p1

"Installing for i386-pc platform.
grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: error: embedding is not possible, but this is required for RAID and LVM install."

(This is also a two-drive level 0 RAID, which naturally further complicates things)

I am going to have to stay logged in until I can reinstall the files on /boot.

Help would be appreciated. :)

---

