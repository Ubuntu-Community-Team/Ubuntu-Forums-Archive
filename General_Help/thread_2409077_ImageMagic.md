---
title: "ImageMagic?"
date: 2018-12-27
forum: General Help
---

### Post by Daveski17 on 2018-12-27
I upgraded to Ubuntu 16.04 LTR from 14.04 LTR yesterday. Everything seems more or less OK but I don't understand why there are two ImageMagick icons here. Is it safe to uninstall this as it seems a tad buggy?

Thanks.

EDIT: I uninstalled the double and have left the one copy. After some research it might be prudent to leave one of them. I still say it's buggy though.

---

### Post by #&amp;thj^% on 2018-12-27
First, before removing it, you should know that you will remove other software that you might need, like parts of the printing system. 
imagemagick may be a dependency for other pieces of software run:
```

apt-cache showpkg imagemagick
```
Now if you are still sure you want to remove it:
```
sudo apt remove --purge imagemagick

```
My suggestion is >>> Don't remove image magic.

---

### Post by Daveski17 on 2018-12-27
> **1fallen said:**
> First, before removing it, you should know that you will remove other software that you might need, like parts of the printing system. 
imagemagick may be a dependency for other pieces of software run:
```

apt-cache showpkg imagemagick
```
Now if you are still sure you want to remove it:
```
sudo apt remove --purge imagemagick

```
My suggestion is >>> Don't remove image magic.

OK thanks. I'm not sure why there were two versions of it installed. I uninstalled one of them from the Software Centre and left the other on the computer. I may have accidentally downloaded the second while I was familiarising myself with the Centre last night.

---

### Post by Autodave on 2018-12-27
16.04 isn't buggy.  Neither is 18.04.  Upgrading from one release to another *is usually* buggy.   At least in my own experience.  I learned a long time ago not to upgrade.  I back everything up on an external source and do clean installs.

---

### Post by Daveski17 on 2018-12-27
> **Autodave said:**
> 16.04 isn't buggy.  Neither is 18.04.  Upgrading from one release to another *is usually* buggy.   At least in my own experience.  I learned a long time ago not to upgrade.  I back everything up on an external source and do clean installs.

Yes, I was contemplating doing exactly that. So far everything seems OK though. I meant that ImageMagick seems a bit buggy, it's more like abandon-ware. So far the Xenial upgrade is working well. I bought this Levono laptop with Trusty preinstalled so I thought I'd chance an 'over the top' upgrade rather than a clean install.

---

### Post by liaata on 2018-12-28
> **Autodave said:**
> 16.04 isn't buggy.  Neither is 18.04.  Upgrading from one release to another *is usually* buggy.   At least in my own experience.  I learned a long time ago not to upgrade.  I back everything up on an external source and do clean installs.

I made the same experience. If you upgrade, you will spend a lot of time fixing the new issues. 
It's better to reinstall

---

### Post by Daveski17 on 2018-12-29
Well, day four and no problems, touch wood lol.

---

### Post by mc4man on 2018-12-29
You had 2 icons because in 16.04 imagemagick installed 2 .desktop files, i.e
/usr/share/applications/display-im6.desktop
/usr/share/applications/display-im6.q16.desktop

Both use the same displayed name & icon, only difference is the Exec= line

In 14.04 there was only the 1st. .desktop installed.  In 18.04 there are no .desktops installed any more.
(- limited value, one can do the same with the display /path/to/file command

---

### Post by Daveski17 on 2018-12-30
> **mc4man said:**
> You had 2 icons because in 16.04 imagemagick installed 2 .desktop files, i.e
/usr/share/applications/display-im6.desktop
/usr/share/applications/display-im6.q16.desktop

Both use the same displayed name & icon, only difference is the Exec= line

In 14.04 there was only the 1st. .desktop installed.  In 18.04 there are no .desktops installed any more.
(- limited value, one can do the same with the display /path/to/file command

OK thanks. That explains it then.

---

### Post by corradoventu on 2018-12-30
```
corrado@corrado-p6-dd-1227:~$ apt policy imagemagick
imagemagick:
  Installed: (none)
  Candidate: 8:6.9.10.14+dfsg-7ubuntu2
  Version table:
     8:6.9.10.14+dfsg-7ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu disco/universe amd64 Packages
corrado@corrado-p6-dd-1227:~$ apt show imagemagick
Package: imagemagick
Version: 8:6.9.10.14+dfsg-7ubuntu2
Priority: optional
Section: universe/graphics
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: ImageMagick Packaging Team <pkg-gmagick-im-team@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 125 kB
Depends: imagemagick-6.q16 (>= 8:6.9.2.10+dfsg-2~)
Homepage: https://www.imagemagick.org/
Task: ubuntustudio-video, ubuntustudio-publishing, ubuntustudio-graphics, ubuntukylin-desktop, ubuntu-budgie-desktop
Download-Size: 14,4 kB
APT-Sources: http://archive.ubuntu.com/ubuntu disco/universe amd64 Packages
Description: image manipulation programs -- binaries
 ImageMagick is a software suite to create, edit, and compose bitmap images.
 It can read, convert and write images in a variety of formats (over 100)
 including DPX, EXR, GIF, JPEG, JPEG-2000, PDF, PhotoCD, PNG, Postscript,
 SVG, and TIFF. Use ImageMagick to translate, flip, mirror, rotate, scale,
 shear and transform images, adjust image colors, apply various special
 effects, or draw text, lines, polygons, ellipses and Bézier curves.
 All manipulations can be achieved through shell commands as well as through
 an X11 graphical interface (display).
 .
 This package include links to channel depth specific binaries and manual
 pages.
 .
 This is a dummy package.  You can safely purge or remove it.

corrado@corrado-p6-dd-1227:~$ 

```

---

### Post by Daveski17 on 2018-12-30
It doesn't have good reviews.

[ATTACH=CONFIG]282042[/ATTACH]

---

