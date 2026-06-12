---
title: "gThumb not seeing images on Nexus 4"
date: 2013-05-19
forum: General Help
---

### Post by Nick Payne on 2013-05-19
gThumb 3.0.2 on 13.04. When I connect my Nexus 4 via USB, it mounts using USB MTP and using the file manager I can see that there are images on the device under the path shown as "Internal storage/DCIM/Camera", but when I start gThumb and ask it to import from the Nexus 4 removable device, it does a folder listing of the Nexus and comes back as empty - no files of type Media are found. The only way to get the images off with gThumb is to select the menu option File / Import From / Folder, then manually select the DCIM/Camera folder on the device, at which point the Files to import window still shows as empty, and then change the file type to show from "Media" to "All files", at which point the jpg files finally show. However, if I select the images and import them, the filenames are garbaged to just numbers - e.g. an image that has the filename "IMG_20130514_144526.jpg" on the Nexus has the filename "1643" (no jpg extension) when imported.

It seems there are two bugs here. Firstly, images on the Nexus 4 are not being detected as such, and secondly, filenames are not being preserved on import. If I connect one of my digital cameras to the PC via USB, then gThumb works correctly - it finds the images on the device and preserves the filenames when importing them.

---

