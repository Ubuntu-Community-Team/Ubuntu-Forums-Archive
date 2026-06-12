---
title: "ISO's burned to USB flagged read-only"
date: 2018-12-21
forum: General Help
---

### Post by unicav on 2018-12-21
I've been working on building some ISO's from source repos and ran into this issue. When trying to change out only a couple files (kernel and system.sfs) on the ISO it can't be done on the USB stick.
Finally I discovered it's only when the USB sticks are created on my Ubuntu-18.04 system. Doesn't matter if it's Etcher, dd, or ISO Master. NO ISO that I burn on the Ubuntu system will ever allow me to edit it again.
Also the USB is never readable on any Windows PC, but I'm guessing that's just because it's creating ext4 instead of fat32 and I haven't added support for ext4 on my Windows box.
The images are bootable on the device I'm testing, I just can't edit them.
If I burn the image on a Windows PC with Rufus it will mount on Windows, Ubuntu and anything else as fully writable.
I've dug through a lot of threads on this issue but everything seems to mainly point to formatting the USB again, and I can't do that, I only want to swap out a couple files on it.
I also have tried editing the ISO then burning to the USB again, but that image won't burn with Etcher due to a warning that it's not a bootable ISO. 
However the same image burned with Rufus will actually boot.
I'd rather just do all the editing/revisions and burning in Ubuntu, but this has had me stumped for weeks.

---

### Post by ajgreeny on 2018-12-21
As far as I'm aware a live system used for installing an operation system is always read only as it creates an ISO_9600 filesystem whether using CD DVD or USB, which I believe is always read only.

See [https://en.wikipedia.org/wiki/ISO_9660](https://en.wikipedia.org/wiki/ISO_9660)

If you want to make any changes to the live system you will have to unpack the archive (the iso file itself) and then do whatever you want to before re-creating the iso archive.
This was once easier than it is now using remastersys but it is no longer being developed so has disappeared from view and my quick search has found no obvious alternative.  Others may know more than I do so wait to see what else comes along.

---

