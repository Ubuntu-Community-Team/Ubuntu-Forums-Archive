---
title: "Broken fonts, most are just boxes, only some display correctly"
date: 2018-06-09
forum: General Help
---

### Post by alejandros714 on 2018-06-09
Currently running lubuntu 18.04 

I was trying to install some truetype dos fonts earlier but somewhere along the line my system wide fonts went from being "monospace 8" to boxes everywhere. I managed to switch temporarily to a font that isn't all boxes but currently most of what I have is unusable. 

I was wondering how exactly I would go about restoring my fonts to a default. 

Running `fc-cache -v` gives me this:

```

[ shockrah ] fc-cache -v
/usr/share/fonts: skipping, existing cache is valid: 0 fonts, 6 dirs
/usr/share/fonts/X11: skipping, existing cache is valid: 0 fonts, 3 dirs
/usr/share/fonts/X11/encodings: skipping, existing cache is valid: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: skipping, existing cache is valid: 89 fonts, 0 dirs
/usr/share/fonts/X11/util: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/cMap: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/cmap: skipping, existing cache is valid: 0 fonts, 5 dirs
/usr/share/fonts/cmap/adobe-cns1: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-gb1: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-japan1: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-japan2: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-korea1: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/opentype: skipping, existing cache is valid: 0 fonts, 2 dirs
/usr/share/fonts/opentype/malayalam: skipping, existing cache is valid: 3 fonts, 0 dirs
/usr/share/fonts/opentype/noto: skipping, existing cache is valid: 24 fonts, 0 dirs
/usr/share/fonts/truetype: skipping, existing cache is valid: 0 fonts, 37 dirs
/usr/share/fonts/truetype/Gubbi: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/Nakula: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/Navilu: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/Sahadeva: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/abyssinica: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/dejavu: skipping, existing cache is valid: 6 fonts, 0 dirs
/usr/share/fonts/truetype/fonts-beng-extra: skipping, existing cache is valid: 6 fonts, 0 dirs
/usr/share/fonts/truetype/fonts-deva-extra: skipping, existing cache is valid: 3 fonts, 0 dirs
/usr/share/fonts/truetype/fonts-gujr-extra: skipping, existing cache is valid: 5 fonts, 0 dirs
/usr/share/fonts/truetype/fonts-guru-extra: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/fonts-kalapi: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/fonts-orya-extra: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/fonts-telu-extra: skipping, existing cache is valid: 2 fonts, 0 dirs
/usr/share/fonts/truetype/kacst-one: skipping, existing cache is valid: 2 fonts, 0 dirs
/usr/share/fonts/truetype/lao: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-assamese: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-bengali: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-devanagari: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-gujarati: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-kannada: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-malayalam: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-oriya: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-punjabi: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-tamil: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-tamil-classical: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/lohit-telugu: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/malayalam: skipping, existing cache is valid: 11 fonts, 0 dirs
/usr/share/fonts/truetype/noto: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/padauk: skipping, existing cache is valid: 4 fonts, 0 dirs
/usr/share/fonts/truetype/pagul: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/samyak: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/samyak-fonts: skipping, existing cache is valid: 3 fonts, 0 dirs
/usr/share/fonts/truetype/sinhala: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/tibetan-machine: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/tlwg: skipping, existing cache is valid: 58 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: skipping, existing cache is valid: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu: skipping, existing cache is valid: 13 fonts, 0 dirs
/usr/share/fonts/type1: skipping, existing cache is valid: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: skipping, existing cache is valid: 35 fonts, 0 dirs
/usr/local/share/fonts: skipping, existing cache is valid: 0 fonts, 0 dirs
/home/shockrah/.local/share/fonts: skipping, no such directory
/home/shockrah/.fonts: skipping, existing cache is valid: 0 fonts, 0 dirs
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/shockrah/.cache/fontconfig: cleaning cache directory
/home/shockrah/.fontconfig: not cleaning non-existent cache directory
fc-cache: succeeded

```

I'm really not sure what to make of this and can't find anyway of diagnosing this so maybe someone here can help me out? Thanks in advance

---

