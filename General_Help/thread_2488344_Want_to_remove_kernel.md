---
title: "Want to remove kernel"
date: 2023-07-03
forum: General Help
---

### Post by pr0ton1c on 2023-07-03
I recently installed a VPN service but it didn't work so I ditched it. However, it left behind a kernel version
62.0.2-1007-low-latency as shown in the following image on the left. This apparently hangs the computer on restart, unless I catch
it during grub. (At the bottom of the image shows my current boot kernel 6.2.0.24-generic):
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292438&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292439&stc=1[/IMG]
The right hand image shows what pops up when I say to remove the 1007-low-latency kernel.
My question is, can I remove the the 6.2.0-1007-low-latency kernel as long as I'm booted into 6.2.0-25-generic?
Thanks

---

### Post by Impavidus on 2023-07-03
It should be no problem.

I suspect you've got a package X that depends on either linux-image-unsigned-6.2.0-1007-lowlatency or linux-signatures-nvidia-6.2.0-1007-lowlatency. You can only remove one when you install the other. Mark that package X for removal first.

---

