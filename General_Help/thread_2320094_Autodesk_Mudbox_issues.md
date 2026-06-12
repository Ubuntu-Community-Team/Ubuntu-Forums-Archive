---
title: "Autodesk Mudbox issues"
date: 2016-04-10
forum: General Help
---

### Post by erik41 on 2016-04-10
Hello,

I am having trouble getting Autodesk Mudbox 2016 to run.
After successfully installing on Ubuntu 14.04 64-bit when trying to run I get the error that it fails to load [COLOR=#000000][FONT=Helvetica Neue Regular]libGeneralImage.so
When running
[/FONT][/COLOR]```
ldd -r libGeneralImage.so

```

I get the following
```

undefined symbol: TIFFWriteEncodedStrip    (./libGeneralImage.so)
undefined symbol: TIFFGetField    (./libGeneralImage.so)
undefined symbol: TIFFSetField    (./libGeneralImage.so)
undefined symbol: TIFFReadRGBAImageOriented    (./libGeneralImage.so)
undefined symbol: TIFFOpen    (./libGeneralImage.so)
undefined symbol: TIFFSetErrorHandler    (./libGeneralImage.so)
undefined symbol: TIFFClose    (./libGeneralImage.so)
undefined symbol: TIFFReadScanline    (./libGeneralImage.so)
undefined symbol: TIFFWriteDirectory    (./libGeneralImage.so)

```

Then I try to create symbolic links to libtiff (as root)
```

ln -s /usr/lib/x86_64-linux-gnu/libtiff.a
ln -s /usr/lib/x86_64-linux-gnu/libtiff.la
ln -s /usr/lib/x86_64-linux-gnu/libtiff.so
ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5
ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5.2.0
ln -s /usr/lib/x86_64-linux-gnu/libtiffxx.a
ln -s /usr/lib/x86_64-linux-gnu/libtiffxx.la
ln -s /usr/lib/x86_64-linux-gnu/libtiffxx.so
ln -s /usr/lib/x86_64-linux-gnu/libtiffxx.so.5
ln -s /usr/lib/x86_64-linux-gnu/libtiffxx.so.5.2.0

```

Then I try to run Mudbox again but I get the same error, I try to reboot with no luck either.

Thank you in advanced

---

