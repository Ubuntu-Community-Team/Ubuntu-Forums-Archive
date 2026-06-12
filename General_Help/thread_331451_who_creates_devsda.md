---
title: "who creates /dev/sda ?"
date: 2007-01-04
forum: General Help
---

### Post by romerun on 2007-01-04
I'm doing a homemade linux bootstrap. I have 2 bootstraps, initrd bootstrap which is small, and the actual bootsrap which will be mounted on on ramdrive to be the actual root system. My problem is, I have a new box with an adaptec raid card, in the process of initrd, it sees /dev/sda*, but when it chroot to the actual boostrap, there's no /dev/sda*. The kernel should have support it because the initrd bootstrap can create /dev/sda*, but for some reason, the actual bootstrap won't generate it. I wonder how the system create these devices ?

---

