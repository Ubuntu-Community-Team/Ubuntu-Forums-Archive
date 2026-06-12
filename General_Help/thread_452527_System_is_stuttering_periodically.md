---
title: "System is stuttering periodically"
date: 2007-05-23
forum: General Help
---

### Post by elexx on 2007-05-23
Hello all,

since days im trying to find out what is actually going on with my system. The problem is, that it stucks every 5-7 seconds for a few milliseconds. It does not matter if im writing a doc or watching a video, even the login screen of wow running cedega.

so i changed RAM, tried vesa, nv and nvidia drivers, played around with my power suppy and the hard disks (mdraid) nothing at all helps. No output in the logs so far that could help me. Everything works fine in Vista. Tried a self built kernel using oldconfig, and (!) seems like stuttering also via bootcd (feisty).

My specs:

Ubuntu feisty 64bit
Core 2 Duo 6600
intel q965 chipset
nvidia 7950gt
DDR"-Ram 1024MB Samsung 
2 x 320gb seagate, raid 1 via mdraid


Any ideas?

---

### Post by rax_m on 2007-05-24
I don't know much about 64-bit linux, but have you tried checking what process might be consuming the most CPU?

---

