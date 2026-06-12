---
title: "Desktop fails after upgrade to Raring"
date: 2013-05-05
forum: General Help
---

### Post by sturdy on 2013-05-05
Hi all,

Everytime I upgrade it seems something goes wrong :( After upgrade to Raring, Unity is broken. I eventually was able to get a workable desktop but my vid card is a Radeon 3850 (RV670) so I understand it is now supported by the open-source xserver-xorg-video-radeon driver. I tried to remove and re-install the driver using Synaptic. Removal worked but now Synaptic tells me the package is broken and I get a similar message when I try to fix the broken package using Synaptic. I am unable to re-install the driver package. I checked dependencies and all except one are okay. The one missing package is xorg-video-abi-13 but that package is not listed by Synaptic and apparently not available for Raring. Now I am lost...can somebody point me in the right direction. TIA.

---

### Post by sturdy on 2013-05-05
Edit to my original...
Just received an update,  I think the name was Ubuntu-Base that updated the radeon drivers and changed the dependency to xorg-video-abi-12 (not 13) but the same problem exists. The file doesn't seem to be available for Raring.

---

### Post by sturdy on 2013-05-07
Well...sometimes the easiest fix is to just reload.

---

