---
title: "Limiting virtual terminal devices (/dev/vcs* /dev/vcsa*)"
date: 2013-09-10
forum: General Help
---

### Post by wtriba2 on 2013-09-10
For a new arm/lucid installation, udev (or other init script) is populating 64 /dev/vcsN and 64 /dev/vcsaN. For my other distro's and platforms the number is typically limited to 12 each. Where do I configure the maximum created at boot? I see a MAX_NR_CONSOLES that can be configured in the kernel, but I shouldn't have to limit that to modify the boot up config.

---

