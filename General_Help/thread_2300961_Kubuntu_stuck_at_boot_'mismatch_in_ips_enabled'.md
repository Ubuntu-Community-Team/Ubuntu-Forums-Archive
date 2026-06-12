---
title: "Kubuntu stuck at boot 'mismatch in ips_enabled'"
date: 2015-10-29
forum: General Help
---

### Post by Rick_van_Hek on 2015-10-29
I installed Kubuntu recently, dual boot, other boot I run Windows 10, so today I installed the latest kubuntu, and today when i restarted it always did this on the screenshot,
But since now It's just stuck at that screen, doesn't boot anymore.. This actually happened after I installed the latest Nvidia driver (the errors already were there, but since i installed latest nvidia driver it also got stuck)
with the command sudo apt-get install Nvidia-current
What should I do?
[IMG]https://scontent-fra3-1.xx.fbcdn.net/hphotos-xtl1/v/t34.0-12/12188585_1063237750387187_1265167807_n.jpg?oh=8d0864e3c20ccb84e78f4bc89b3593f0&oe=563531EC[/IMG]

---

### Post by SeijiSensei on 2015-10-29
I'd start over and not install the NVIDIA driver until everything else works.  That error concerns the DRM library in the Intel graphics firmware.  I bet you have a "hybrid" machine with both an Intel and an NVIDIA card.  See if you can turn off the Intel adapter in the BIOS before installing Kubuntu.

---

