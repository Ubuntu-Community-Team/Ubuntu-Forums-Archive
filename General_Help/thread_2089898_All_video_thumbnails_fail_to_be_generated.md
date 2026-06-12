---
title: "All video thumbnails fail to be generated"
date: 2012-11-30
forum: General Help
---

### Post by Prodoc on 2012-11-30
Not a single video thumbnail is being generated and shown in Nautilus. The folder *~/.cache/thumbnails/fail/gnome-thumbnail-factory/* keeps getting filled for all of them (.avi, .mkv, .m4v, etc.).

I tried removing all the thumbnails from the folder, reinstalling the gstreamer-plugins-... and totem packages, changing the thumbnail settings (Always, 4 GB) in the Preview section of the Nautilus preferences. All to no avail. Some recommend to install packages like libxine1 and ffmpegthumbnailer but this didn't not solve it either.

There used to be an *.xsession-errors* error log file generated in the home folder in previous version of Ubuntu but that doesn't seem to be the case any more.

I'm running Ubuntu 12.10 GNOME remix (x64) with the GNOME3 ppa packages installed.

What could be the cause of the problem and how can I fix it?

---

