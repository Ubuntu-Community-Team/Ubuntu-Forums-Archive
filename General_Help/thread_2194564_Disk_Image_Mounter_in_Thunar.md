---
title: "Disk Image Mounter in Thunar"
date: 2013-12-19
forum: General Help
---

### Post by garyzw on 2013-12-19
The Disk Image Mounter was working great in Thunar Xubuntu last week so i try it last night and it does not mount the iso any more? Any help would be much appreacated, see attached screenshot.

---

### Post by Toz on 2013-12-19
For reference, "Disk Image Mounter" is gnome-disk-image-mounter from the "gnome-disk-utility" package.

What happens if you run it from the command prompt? Do you get any error messages?
```
gnome-disk-image-mounter /path/to/iso/file
```
...(change /path/to/iso/file to the real path to your iso file).

I installed it here in xubuntu 13.10 and its working fine so its probably not a problem with the package itself.

---

### Post by garyzw on 2013-12-19
Thanks for the Reply Toz. i ran it from the command prompt and got no error messages, nothing at all so I tried another ISO and it mounted just fine-- so it was a corrupt ISO-- thanks for your help.

---

