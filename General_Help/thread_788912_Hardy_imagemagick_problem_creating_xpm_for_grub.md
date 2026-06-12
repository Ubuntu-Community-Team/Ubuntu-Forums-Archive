---
title: "Hardy imagemagick problem creating xpm for grub"
date: 2008-05-10
forum: General Help
---

### Post by gasolino_ on 2008-05-10
I have a strange problem: I'm tryng to convert some jpg to xpm with the common command
```
$ convert -resize 640x480\! -colors 14 picture.jpg picture.xpm
```
It looks good (well, 14 colors, obviously) viewing with display, eog, gthumb, GIMP. Then gzip and the other stuff. Well, this image loads as splashimage, but in GRUB colors are all wrongs, as my PC has assumed some LSD. Loading the same picture with GIMP and saving (without any modify) results in good colors with GRUB. How is it possible?
Identify give this result:
```

$ identify YaquinaHeadLighthouseGimp.xpm 
YaquinaHeadLighthouseGimp.xpm XPM 640x480 640x480+0+0 DirectClass 16-bit 302.164kb

$ identify YaquinaHeadLighthouseMagick.xpm  
YaquinaHeadLighthouseMagick.xpm XPM 640x480 640x480+0+0 PseudoClass 14c 16-bit 302.283kb

```
All I can see is that one is DirectClass, the other PseudoClass. I looked for a way to force DirectClass, but nothing works. Someone can try this? Is this a bug in ImageMagick? I'm using Hardy Heron.
```
$ convert -version
Version: ImageMagick 6.3.7 02/19/08 Q16 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2008 ImageMagick Studio LLC
```

[UPDATE] To try splashimage without reboot see [http://wiki.debian.org/Grub/SplashImage](http://wiki.debian.org/Grub/SplashImage) "Testing with QEMU". Thanks.

**SOLUTION**
The problem is solved with the option -depth, the command become:
```

$ convert picture.jpg -resize 640x480\! -colors 14 -depth 8 picture.xpm

```
Without this option IM created a 16-bit image, whereas GIMP created as default a 8-bit image... Not a problem of DirectClass or PseudoClass. I could realize only with identify -verbose, which says the true depth... damn it!

---

### Post by angry_johnnie on 2008-05-29
Interesting... I'd been wondering why it didn't work, and just decided to create them in Feisty while it was fixed... ah the lazyness! :p  Thanks for figuring this out.

---

