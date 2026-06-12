---
title: "How to set wallpaper for a custom distro? - Help needed!"
date: 2013-05-04
forum: General Help
---

### Post by Aleksej on 2013-05-04
Hi! Can somebody tell me where is the file that stores information about the path of the image that would be a default wallpaper? I'm building a custom distro with remastersys, and I would like to set a custom wallpaper. Thanks!

---

### Post by deadflowr on 2013-05-04
Clueless as to where the default first start-up wallpaper is loaded from, but the system wallpapers are stored in /usr/share/backgrounds.
And the file the system reads is an xml file in the /usr/share/gnome-background-properties folder.
Whatever is listed in the various xml files will show up in  appearance> wallpapers.

I copied an xml file and changed out the images listed with my own and then saved a copy, renamimg it mywallpaper.xml.
I also made a background directory, /backgrounds. The paths of the file in the xml go to the images in the /backgrounds directory.
I then save a copy in a backup place so when I do reinstalls or installs I can move a copy in and use my wallpapers system-wide.

---

