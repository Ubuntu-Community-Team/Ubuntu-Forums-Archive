---
title: "Help on Ufraw and exiv2."
date: 2007-09-06
forum: General Help
---

### Post by alelinuxbsd on 2007-09-06
I have realized a package of the last release of ufraw 0.12.1 for the Ubuntu Edgy but i have one problem, I can export exif data.
The big difference within the precedence release is that:
configure: build GIMP plug-in: yes
configure: build CinePaint plug-in: no
configure: EXIF support using exiv2: yes
configure: JPEG support: yes
configure: PNG support: yes
configure: TIFF support: yes
configure: gzip compressed raw support: yes
configure: bzip2 compressed raw support: no
configure: Scrolling in preview using GtkImageView: no

Yes the exif support using exiv2 is present but when i open a photo with ufraw i obtain the message:
"Exif data will not be sent to output"

I have also create a package of exiv2 0.15 but the problem persist.:(

Someone can help me?

Thank in advance, Alessandro

Note:
I'm using a x32 version.

---

