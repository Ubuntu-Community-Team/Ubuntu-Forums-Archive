---
title: "About ImageMagick"
date: 2022-12-22
forum: General Help
---

### Post by satimis on 2022-12-22
**[COLOR="#FF0000"]Ubuntu 22.04 desktop[/COLOR]**
I need to install the latest version of ImageMagick

$ apt policy imagemagick```

imagemagick:
  Installed: (none)
  Candidate: 8:6.9.10.23+dfsg-2.1ubuntu11.4
  Version table:
     8:6.9.10.23+dfsg-2.1ubuntu11.4 500
        500 http://hk.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     8:6.9.10.23+dfsg-2.1ubuntu11 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```

ImageMagick is not installed.

But it is very strange to me;

$ convert -version```

Version: ImageMagick 6.9.10-23 Q16 x86_64 20190101 https://imagemagick.org
Copyright: © 1999-2019 ImageMagick Studio LLC
License: https://imagemagick.org/script/license.php
Features: Cipher DPC Modules OpenMP 
Delegates (built-in): bzlib djvu fftw fontconfig freetype jbig jng jpeg lcms lqr ltdl lzma openexr pangocairo png tiff webp wmf x xml zlib

```

ImageMagick 6.9.10-23 is already installed.

$ which magick
no output ?

$ which convert```

/usr/bin/convert

```

Please help.  Thanks

Regards

---

### Post by HermanAB on 2022-12-22
Hmm, try running those commands with sudo.

---

### Post by satimis on 2022-12-22
> **HermanAB said:**
> Hmm, try running those commands with sudo.

$ sudo convert -version > convert.txt

$ sudo which magick
no output

convert.txt is attached here

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
Tried again

$ sudo apt policy imagemagick
[sudo] password for satimis: ```

imagemagick:
  Installed: 8:6.9.11.60+dfsg-1.3build2
  Candidate: 8:6.9.11.60+dfsg-1.3build2
  Version table:
 *** 8:6.9.11.60+dfsg-1.3build2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

$ sudo convert -version | more```

Version: ImageMagick 6.9.11-60 Q16 x86_64 2021-01-25 https://imagemagick.org
Copyright: (C) 1999-2021 ImageMagick Studio LLC
License: https://imagemagick.org/script/license.php
Features: Cipher DPC Modules OpenMP(4.5) 
Delegates (built-in): bzlib djvu fftw fontconfig freetype heic jbig jng jp2 jpeg
 lcms lqr ltdl lzma openexr pangocairo png tiff webp wmf x xml zlib

```

Regards

---

### Post by Impavidus on 2022-12-22
/usr/bin/convert isn't part of any package. It's a symlink via /etc/alternatives/convert to /usr/bin/convert-im6.q16. That file is, according to```
dpkg --search /usr/bin/convert-im6.q16
```part of the package imagemagick-6.q16, which is a dependency of imagemagick.

---

