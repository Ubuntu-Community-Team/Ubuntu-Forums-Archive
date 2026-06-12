---
title: "Mount / Unmount CD Image Script Issues"
date: 2007-03-15
forum: General Help
---

### Post by AegisTalons on 2007-03-15
Hey Everyone,

I just switched over to Ubuntu recently, and IMO it has a steep learning curve, but once you get the hang of it, it works wonderful.

Anyways, I want to mount/unmount CD images on Ubuntu. I have CDemu working fine. I found a nice wiki on a Nautilus Script for general purpose mounting/unmounting of all different types of CD images. 

[http://doc.gwos.org/index.php/Mount_ISO_script]("http://doc.gwos.org/index.php/Mount_ISO_script")

Now, I have it in the Nautilus-Script folder as instructed, but when I right click on an image file and select scripts, and mount-cdimage, nothing happens. I even uncommented the code so a link would be place on my desktop of the mounted cd image. Any ideas would be great.

Thanks in advance

---

### Post by lloyd_b on 2007-03-16
First off, did you make the scripts executable (via the "chmod" command)?
```
chmod +x ~/.gnome2/nautilus-scripts/iso-mount.bash
chmod +x ~/.gnome2/nautilus-scripts/iso-umount.bash
```

If that wasn't it, try running the scripts from a terminal window:
```
~/.gnome2/nautilus-scripts/iso-mount.bash
```
and see what the result is.  This should at least give you an error message that will help identify the problem.

Lloyd B.

---

