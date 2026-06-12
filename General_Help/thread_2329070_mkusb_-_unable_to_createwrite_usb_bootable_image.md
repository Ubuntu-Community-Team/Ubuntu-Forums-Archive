---
title: "mkusb - unable to create/write usb bootable image"
date: 2016-06-27
forum: General Help
---

### Post by Geoffrey_Arndt on 2016-06-27
Am trying, via the mkusb app, to create a bootable usb v2 flash-stick.    Am running Ubuntu 15.10 and using the repo version of mkusb (10.6.3).

I have a valid iso.image on my hdd (sdb).   I know the image is good as had a successful write to the same usb flashstick (v2) (Kingston Traveler 8GB DTSE9) using Etcher.   So, I don't believe there are issues with the iso or the flash-stick.  There seems to be an issue with the way the usb is mounted (or perhaps how the source file on sdb is mounted?).   

Errors are:
>  No disk-name string found in the iso file (it does have a proper name string)
>  Gtk Message:   Gtk dialog mapped with a transient parent.  This is discouraged.
>  The ISO file should be loop mounted on a temporary read-only device

[ATTACH]269829[/ATTACH]

hmm, the above seems to be an incomplete file, or a new one has over-written it as I took another look at the process of running mkusb but didn't complete the steps.   So, pls refer to the error messages I've manually typed in above.   Thanks.

---

