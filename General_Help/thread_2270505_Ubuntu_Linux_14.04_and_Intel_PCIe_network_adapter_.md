---
title: "Ubuntu Linux 14.04 and Intel PCIe network adapter issues"
date: 2015-03-23
forum: General Help
---

### Post by scalrtn on 2015-03-23
Hello,

I'm running Ubuntu 14.04 on an older desktop Minitower, where I recently had to add an additional network adapter (Intel PCI Express) because the on board network adapter that came with the computer was apparently fried due to an electrical surge during a storm.

After disabling the onboard network adapter in the BIOS and rebooting the machine with the adapter, the OS detected the card and made it active.   (I downloaded no drivers from Intel for it - Is Ubuntu using some generic driver, or have drivers been incorporated into the kernel for the known Intel adapters?)   Everything works fairly well - for the most part.  

Occasionally gmail appears to "hang" when switching folders, YouTube videos get hung, Facebook hangs during assorted operations, Google image searches are slow etc.  The settings for the adapter appear limited in Network setup (I can change MTU size, but that's about it, though I'm unsure what value to institute - I think the default size may be 1500, but I'm not sure, since the setting in Ubuntu is "automatic").

I'm not sure if the issues I'm seeing are related to an incorrect/deficient MTU size, or if I in fact would need to pull and install a driver from Intel.  Can anyone comment?

-- Thanks

---

