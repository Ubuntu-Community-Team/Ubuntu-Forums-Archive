---
title: "Imagemagick doesn't appear to install convert?"
date: 2014-10-28
forum: General Help
---

### Post by mike-feldmeier on 2014-10-28
I'm running on Xubuntu, trying to capture a screencast to an animated gif.  Given various posts I'm going the route of recordmydesktop + mplayer + imagemagick [convert] (if anyone has a better recommendation, please let me know).

When I try to run "convert" from the command line, I get:

[FONT=courier new]mike@mike-acer:~$ convert output/* output.gif[/FONT]
[FONT=courier new]The program 'convert' can be found in the following packages:[/FONT]
[FONT=courier new] * imagemagick[/FONT]
[FONT=courier new] * graphicsmagick-imagemagick-compat[/FONT]
[FONT=courier new]Try: sudo apt-get install <selected package>[/FONT]

However, 

[FONT=courier new]mike@mike-acer:~$ sudo apt-get install imagemagick[/FONT]
[FONT=courier new]Reading package lists... Done[/FONT]
[FONT=courier new]Building dependency tree       [/FONT]
[FONT=courier new]Reading state information... Done[/FONT]
[FONT=courier new]imagemagick is already the newest version.[/FONT]
[FONT=courier new]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]

The info for the package is:

[FONT=courier new]mike@mike-acer:~$ apt-cache show imagemagick[/FONT]
[FONT=courier new]Package: imagemagick[/FONT]
[FONT=courier new]Priority: optional[/FONT]
[FONT=courier new]Section: graphics[/FONT]
[FONT=courier new]Installed-Size: 448[/FONT]
[FONT=courier new]Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>[/FONT]
[FONT=courier new]Original-Maintainer: ImageMagick Packaging Team <pkg-gmagick-im-team@lists.alioth.debian.org>[/FONT]
[FONT=courier new]Architecture: amd64[/FONT]
[FONT=courier new]Version: 8:6.7.7.10-6ubuntu3[/FONT]
[FONT=courier new]Depends: libc6 (>= 2.2.5), libmagickcore5 (>= 8:6.7.7.10), libmagickwand5 (>= 8:6.7.7.10), hicolor-icon-theme[/FONT]
[FONT=courier new]Recommends: libmagickcore5-extra, ghostscript, netpbm[/FONT]
[FONT=courier new]Suggests: imagemagick-doc, autotrace, cups-bsd | lpr | lprng, curl, enscript, ffmpeg, gimp, gnuplot, grads, groff-base, hp2xx, html2ps, libwmf-bin, mplayer, povray, radiance, sane-utils, texlive-base-bin, transfig, xdg-utils, ufraw-batch[/FONT]
[FONT=courier new]Filename: pool/main/i/imagemagick/imagemagick_6.7.7.10-6ubuntu3_amd64.deb[/FONT]
[FONT=courier new]Size: 188098[/FONT]
[FONT=courier new]MD5sum: 46f2c3d4684c8583825589719325b7ba[/FONT]
[FONT=courier new]SHA1: 0ed69f44cfe44528fd2d5bb89601051803674427[/FONT]
[FONT=courier new]SHA256: 3c1b06f6c117bdef5545cd56d1d9a7373851f371950709bad7a3f0c47feaf2df[/FONT]
[FONT=courier new]Description-en: image manipulation programs[/FONT]
[FONT=courier new] ImageMagick is a software suite to create, edit, and compose bitmap images.[/FONT]
[FONT=courier new] It can read, convert and write images in a variety of formats (over 100)[/FONT]
[FONT=courier new] including DPX, EXR, GIF, JPEG, JPEG-2000, PDF, PhotoCD, PNG, Postscript,[/FONT]
[FONT=courier new] SVG, and TIFF. Use ImageMagick to translate, flip, mirror, rotate, scale,[/FONT]
[FONT=courier new] shear and transform images, adjust image colors, apply various special[/FONT]
[FONT=courier new] effects, or draw text, lines, polygons, ellipses and Bézier curves.[/FONT]
[FONT=courier new] All manipulations can be achieved through shell commands as well as through[/FONT]
[FONT=courier new] an X11 graphical interface (display).[/FONT]
[FONT=courier new]Description-md5: 7c91199cdb23d3f0345a662d072b5a37[/FONT]
[FONT=courier new]Multi-Arch: foreign[/FONT]
[FONT=courier new]Homepage: [http://www.imagemagick.org/](http://www.imagemagick.org/)[/FONT]
[FONT=courier new]Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)[/FONT]
[FONT=courier new]Origin: Ubuntu[/FONT]
[FONT=courier new]Supported: 5y[/FONT]
[FONT=courier new]Task: ubuntu-usb, kubuntu-full, kubuntu-active-full, edubuntu-desktop-gnome, edubuntu-usb, ubuntustudio-video, ubuntustudio-photography, ubuntustudio-graphics[/FONT]

Does anybody know what's going on with this?  Is it a package issue, or user issue?

Thanks,
Mike

---

### Post by ian-weisser on 2014-10-28
Check and see if 'convert' is really installed. Follow the links until you find the real binary provided by the imagemagick package:
```
me@me:~$ which convert
/usr/bin/convert

me@me:~$ ls -l /usr/bin/convert
lrwxrwxrwx 1 root root 25 Jul  1 18:58 /usr/bin/convert -> /etc/alternatives/convert

me@me:~$ ls -l /etc/alternatives/convert
lrwxrwxrwx 1 root root 20 Jul  1 18:58 /etc/alternatives/convert -> /usr/bin/convert.im6

me@me:~$ ls -l /usr/bin/convert.im6 
-rwxr-xr-x 1 root root 5580 Aug 21 09:26 /usr/bin/convert.im6

me@me:~$ dpkg -S /usr/bin/convert.im6 
imagemagick: /usr/bin/convert.im6
```

If the links are unbroken and the binary is there, then we'll look at your PATH variable.
If the links are broken or the binary is missing, then try reinstalling imagemagick.

---

### Post by longwest on 2015-06-04
> **ian-weisser said:**
> Check and see if '[[COLOR="#333333"]convert[/COLOR]]("http://www.rasteredge.com/how-to/csharp-imaging/tiff-converting/")' is really installed. Follow the links until you find the real binary provided by the imagemagick package:
```
me@me:~$ which convert
/usr/bin/convert

me@me:~$ ls -l /usr/bin/convert
lrwxrwxrwx 1 root root 25 Jul  1 18:58 /usr/bin/convert -> /etc/alternatives/convert

me@me:~$ ls -l /etc/alternatives/convert
lrwxrwxrwx 1 root root 20 Jul  1 18:58 /etc/alternatives/convert -> /usr/bin/convert.im6

me@me:~$ ls -l /usr/bin/convert.im6 
-rwxr-xr-x 1 root root 5580 Aug 21 09:26 /usr/bin/convert.im6

me@me:~$ dpkg -S /usr/bin/convert.im6 
imagemagick: /usr/bin/convert.im6
```

If the links are unbroken and the binary is there, then we'll look at your PATH variable.
If the links are broken or the binary is missing, then try reinstalling [[COLOR="#333333"]image[/COLOR]]("http://www.rasteredge.com/dotnet-imaging/")magick.
Thank you so much.
The code you posted is really helpful.:p

---

