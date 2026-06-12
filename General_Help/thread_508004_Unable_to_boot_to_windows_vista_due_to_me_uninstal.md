---
title: "Unable to boot to windows vista due to me uninstalling ubuntu"
date: 2007-07-23
forum: General Help
---

### Post by BlackChaos on 2007-07-23
I recently installed unbuntu on my windows vista box so i was able 2 dual boot between the two but since i was running out of space so i decided to delete the ubuntu partition to make more hdd space for windows vista so i deleted the ubuntu partition and now when i try to boot my pc it gives me a grub error 22, i am currently using the ubuntu live cd man i swear this cd is so useful, plz help cause i do not want to have to reinstall windows.

---

### Post by markusf21 on 2007-07-23
Try using super grub disk to fix your MBR
[http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download")

---

### Post by astralsin on 2007-07-23
if you have your windows disc, boot it up and go to the recovery console.  you'll get a dos prompt, type in 
```

fixmbr c:
fixboot c:

```

or you could always just reinstall ubuntu :)

---

