---
title: "Kernel updates screwing menu.lst"
date: 2007-04-16
forum: General Help
---

### Post by namityadav on 2007-04-16
Hi guys. Quick question .. My HDD is partitioned in sda1 - swap, sda2 - /, sda3 - windows. Every time the kernel updates, it rewrites hd0,1 in the menu.lst file to hd0,2 (Which is Windows .. hence wrong). Can anyone please tell me how I can fix this?

Currently after every kernel update, I have to manually edit the menu.lst file to switch all hd0,2 to hd0,1 before rebooting. Otherwise the boot fails as it doesn't find / on sda3 (Obviously)

---

### Post by Bigbluecat on 2007-04-16
I think in menu.lst you need to set groot= to your root partition (/).

Then maybe also set updatedefultentry=true so that it maintains the default boot option.

---

### Post by namityadav on 2007-04-16
groot was set to hd0,2 .. but was commented out. I don't know how grub determines the "/" partition .. but it was obviously getting it wrong.

I have set groot to hd0,1 and I am very positive that this is going to work now. Thanks a lot for the help !

---

