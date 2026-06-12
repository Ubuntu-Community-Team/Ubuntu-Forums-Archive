---
title: "Fonts in 18.04"
date: 2018-08-30
forum: General Help
---

### Post by merlinus on 2018-08-30
I haved many fonts installed that do not show up in Libre Office after upgrading to 18.04.  They show up as installed in Applications/Accessories/Fonts.  Any ideas as to why, and how this issue can be resolved?

---

### Post by ajgreeny on 2018-08-30
Are those fonts installed in the system **/usr/share/fonts** folder or in another user's home?
Have you updated the fonts cache with command ```
sudo fc-cache -f -v
```

---

### Post by merlinus on 2018-08-30
Hi, and thanks for your reponse -- much appreciated!  The fonts are indeed in a subfolder of /usr/share/fonts.  They appear to be type 1 gsfonts.

But nothing changed after running sudo fc-cache -f -v

I closed down Libreoffice and opened it again.  And I logged out and back in again.

Here is the output of the terminal command:

```
/usr/share/fonts: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 89 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cMap: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 5 dirs
/usr/share/fonts/cmap/adobe-cns1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-gb1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-japan1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-japan2: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-korea1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/opentype: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/opentype/mathjax: caching, new cache contents: 24 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/truetype/dejavu: caching, new cache contents: 22 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/liberation: caching, new cache contents: 16 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 61 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/merlin/.local/share/fonts: caching, new cache contents: 10 fonts, 0 dirs
/home/merlin/.fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/home/merlin/.cache/fontconfig: cleaning cache directory
/home/merlin/.cache/fontconfig: invalid cache file: 2cd17615ca594fa2959ae173292e504c-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 95530828ff6c81d309f8258d8d02a23e-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 57e423e26b20ab21d0f2f29c145174c3-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 30829fa25452a46451e813d634d7f916-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 56cf4f4769d0f4abc89a4895d7bd3ae1-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: d3e5c4ee2ceb1fc347f91d4cefc53bc0-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: d52a8644073d54c13679302ca1180695-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 188ac73a183f12857f63bb60a4a6d603-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 4be9850f182b35c1350b6bbf2e42601c-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: d589a48862398ed80a3d6066f4f56f4c-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 3047814df9a2f067bd2d96a2b9c36e5a-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: e52a45a1c8c8fe895fc0fc8c4e6999b8-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 4794a0821666d79190d59a36cb4f44b5-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: fe547fea3a41b43a38975d292a2b19c7-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 1c2c2997deddd45e0296fa5a60917b7d-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: 3830d5c3ddfd5cd38a049b759396e72e-le64.cache-7
/home/merlin/.cache/fontconfig: invalid cache file: f1f2465696798768e9653f19e17ccdc8-le64.cache-7
/home/merlin/.fontconfig: not cleaning non-existent cache directory
fc-cache: succeeded
```

---

### Post by Holger_Gehrke on 2018-08-30
Support for Type 1 Postscript fonts was dropped from LibreOffice in version 5.3 when the font rendering was switched to HarfBuzz. That switch was made mainly for the sake of internationalization, Harfbuzz does the right thing for more writing systems than any other renderer.

Holger

---

### Post by merlinus on 2018-09-01
Thanks for all the info.  I found several free ttf fonts on the Net that pretty much can replace the Type 1's.

---

