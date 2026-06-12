---
title: "Focal, Mesa and Vulkan"
date: 2021-02-02
forum: General Help
---

### Post by tmlake on 2021-02-02
Hello friends,

I've been using Bionic for a while and every Mesa update didn't include mesa-vulkan-drivers installation, but it is 
available as an optional manual install.

Just migrated to Focal and noticed it's newest Mesa 20 has vulkan support fully integrated.
According to this:

"Mesa 20 supports the Vulkan 1.2 graphics ... Mesa 19.2.x lists Vulkan 1.1.2 as the supported version but most of the 
extensions added to the Vulkan 1.2 specification are there as optional extensions. Vulkan 1.2 made previously optional 
extensions mandated parts of the new core specification."

[https://linuxreviews.org/Mesa_20.0.0_Is_Released](https://linuxreviews.org/Mesa_20.0.0_Is_Released)

So, there was I trying to ```
sudo apt remove libvulkan1 mesa-vulkan-drivers
```
 like I usually do on Bionic, but now Focal tells me it's not possible to remove vulkan packages without some 50 more other packages, 
almost the entire system including all xorg and gnome packages and even ubuntu-desktop. 
I uninstalled them all and tried to reinstall, setting vulkan on *hold*, but it wasn't possible without it.

So my question is simple, vulkan is now deep within the system and cannot really be removed?

If not, that's ok I'll just continue to hang around with Bionic.

---

### Post by tmlake on 2021-02-04
Can someone please perform a quick terminal check?

---

