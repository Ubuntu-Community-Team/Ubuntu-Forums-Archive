---
title: "Proper way of updating live CD squashfs"
date: 2024-10-14
forum: General Help
---

### Post by tmontney2 on 2024-10-14
I have a live CD on USB that's customized and will run from RAM. As of Ubuntu 20, my procedure was as follows:

[LIST=1]
[*]Mount the ISO and copy filesystem.squashfs
[*]Unsquash and chroot
[*]Add/update/remove programs as needed
[*]Squash, write the ISO to a USB, and replace the squashfs file
[*]Update grub so that it has a menu entry with the parameter "toram"
[/LIST]

With Ubuntu 24, there are multiple squashfs files. After updating the one listed as "minimal", booting gets hung up on "kerneloops".

If one wanted to customize their live CD to run from RAM, what's the proper way?

---

