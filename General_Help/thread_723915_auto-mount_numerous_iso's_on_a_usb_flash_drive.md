---
title: "auto-mount numerous iso's on a usb flash drive"
date: 2008-03-14
forum: General Help
---

### Post by RoyRP216 on 2008-03-14
I have a usb flash drive with numerous ISO's on it. I am wonder if there is any way I can have these all mount to specific directories automatically when I plug in the drive?

**Example: ** I have a usb flash drive containing the following files: one.iso, two.iso, three.iso, four.iso. I plug in the usb drive. It is automatically mounted like normal, as well as each iso to /media/cd1, /media/cd2, etc.

Thanks for help in advance!

P.S. I'm new here and this is my first post.

---

### Post by chadeldridge on 2008-03-14
I would assume you can just add those ISO images after the USB mount in your fstab... it should work, but I have never tried to chain mount things like that before where there is a dependency for something before you mount the next.

Here is the format for your fstab if you want to try it out.

[http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)

---

### Post by RoyRP216 on 2008-03-14
Thanks, I'll try that and see if it works.

---

