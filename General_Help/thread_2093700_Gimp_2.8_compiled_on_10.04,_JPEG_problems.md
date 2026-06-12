---
title: "Gimp 2.8 compiled on 10.04, JPEG problems"
date: 2012-12-11
forum: General Help
---

### Post by menth1979 on 2012-12-11
I followed these instructions
[http://ubuntuforums.org/showthread.php?t=1982183](http://ubuntuforums.org/showthread.php?t=1982183)

and I managed to compile Gimp on Lucid, however it can't open JPEGs, it says "Wrong JPEG library version: library is 62, caller expects 80".

If I delete libjpeg.so.62 and libjpeg.so.62.0.0 in /usr/lib64 and I make a symlink named libjpeg.so.62 to /usr/local/lib/libjpeg.so.8.0.2 the new Gimp can open JPEGs, but the rest of the applications (like Image Viewer, PDF reader, etc. Firefox is still working) stop working.

I need to tell the new Gimp to read the right library. How?

Found! I made a symlink named libjpeg.so.62 to libjpeg.so.8 into the alternative lib folder (the one setted with LD_CONFIG_LIBRARY). I discovered that Gimp uses small executables in order to open various kind of images. The one responsible for the JPEG opening is file-jpeg. I used the ldd command on it and I discovered that one library was missing in the alternative lib folder, so I made the link. Now it's working.

---

