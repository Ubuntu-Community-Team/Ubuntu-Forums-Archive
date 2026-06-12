---
title: "iPhone photos web upload - wrong orientation"
date: 2013-06-26
forum: General Help
---

### Post by gnjepar on 2013-06-26
Hello,

Former W7Ult user, went to Mint 15 Mate but encountered gvfs problem so back to Ubuntu LTS releases :)

I'm having the same problem as creator of [this]("http://ubuntuforums.org/showthread.php?t=1457699") thread.

To specify even further. Nautilus and default image preview software read the orientation correctly and show the image as it was taken but when I want to upload it to a web site (tried many, it's not web related problem) the file chooser previews them always in landscape mode not respecting the actual orientation and after I choose my images they get uploaded the same way - landscaped :(

This is how it's seen:
[[IMG]http://www.deviantpics.com/images/2013/06/26/slika2eHRJl.th.png[/IMG]]("http://www.deviantpics.com/image/CTF")

This is how it's previewed and uploaded:
[[IMG]http://www.deviantpics.com/images/2013/06/26/slika1UgriI.th.png[/IMG]]("http://www.deviantpics.com/image/CTy")

I'm using chrome, in firefox it does not preview at all.

I've tried using gconf and dconf editors but can not see any options related to this problem. I've googled a lot and found out it's a gtk+2.0 responsibility to preview images in file chooser so I installed gtk+3.0 with ```
sudo apt-get install gtk+3.0
``` but nothing changed. 

I'm running a clean install of 12.04 LTS with gnome-panel (GNOME classic).

**Please help because 90% of usage time on this machine is going to be image upload.**

---

### Post by gnjepar on 2013-06-26
Problem solved, I did clean install of Mint 13.

---

### Post by gnjepar on 2013-06-27
Nope, not solved. After an update problem reappeard again.

---

### Post by gnjepar on 2013-06-27
I've made progress and resolved the issue. I'll sum it up for anyone having the same issues.

Problem existed only for images downloaded from iPhone5 and iPhone4S devices (don't have any other iPhone so don't know for 4, 3G...), images from any other device like digital camera or Nokia E71 were presented with no problem while uploading.

I used a custom script to "auto orient" all of my images in one folder with imagemagick program. Use ```
-auto-orient
``` switch with ```
convert
``` command to repair stupidity of Apple people. After that images display correctly in both Nautilus and file-chooser dialog while uploading.

For newbs like me (for one pic only):
```
sudo apt-get install imagemagick
convert image.jpg -auto-orient oriented-image.jpg
```

I'll post my whole script if there are requests to do so.

---

