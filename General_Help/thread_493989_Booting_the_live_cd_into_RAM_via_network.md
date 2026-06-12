---
title: "Booting the live cd into RAM? via network"
date: 2007-07-06
forum: General Help
---

### Post by 13ojo on 2007-07-06
My PXe looks like this....
```

LABEL Mythbuntu
    MENU LABEL Mythbuntu
    KERNEL /Mythbuntu/casper/vmlinuz
    APPEND vga=normal  initrd=/Mythbuntu/casper/initrd.gz root=/dev/ram0

```

irrelevant stuff omiited.

When i try to boot this i get.

/dev/ram0: unknown volume type?

then

 ```
mount : mounting /sys on /root/sys failed : No such file or directory.
mount : mounting /sys on /root/sys failed : No such file or directory.

```

at which point it drops into ASH. What do i need to fix here hey?, i want to get the live cd (or Mythbuntu, very similar stuff here, eg errors occur at same places) to boot up, so i can use it to install (live cd from the cd crashes lots... cdrom is rather dodgy, plus machine doesnt like it with the 128mbram i think it has).

---

