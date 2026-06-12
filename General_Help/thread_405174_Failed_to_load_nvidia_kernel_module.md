---
title: "Failed to load nvidia kernel module"
date: 2007-04-09
forum: General Help
---

### Post by Viper666 on 2007-04-09
after i compiled a kernel when i try using it it displays "Failed to load nvidia kernel module" i tryed reinstalling the drivers (9631) but they wont compile on the kernel?

what did i do wrong and if i can make it work???

---

### Post by energiya on 2007-04-11
Uninstall your video drivers from the old kernel (also nvidia restricted modules), then install them again, when your computer runs on your new kernel. That did the job for me. You could also compile the video driver from nvidia.com. I find this method easyer (even thow it needs a little tweaking)

---

