---
title: "help making a custom ubuntu usb"
date: 2014-01-25
forum: General Help
---

### Post by rxlord on 2014-01-25
hey from my ubuntu live usb i copied filesystem.squashfs 
and ran this command to unpack it:

unsquashfs filesystem.squashfs

after that i copied my system's /var/cache/apt folder to the /var/cache/apt folder of the unpacked sqashfs
then i repack the contents of squashfs using this command:

mksquashfs squashfs-root filesystem.squashfs -b 1024k -comp xz -Xbcj x86 -e boot

and placed in my live usb but when i boot into my usb it shows a blackscreen after the ubuntu screen.

---

