---
title: "A few scalpel headers"
date: 2018-07-13
forum: General Help
---

### Post by rufuz2 on 2018-07-13
Recently I needed to use sleuthkit's [scalpel]("https://github.com/sleuthkit/scalpel") to recover some video files and dove into a few filetypes to extract their headers and footers. As scalpel doesn't have a forum and I don't know where else I should post this, I'll put it here since this could be useful to someone. If you know of a better place to post this, just let me know. 

Adobe Premiere Pro 2.0 *.prproj* header: 
```
3C 3F 78 6D 6C 20 76 65 72 73 69 6F 6E 3D 22 31 
2E 30 22 20 65 6E 63 6F 64 69 6E 67 3D 22 55 54 
46 2D 38 22 3F 3E 0A 3C 50 72 65 6D 69 65 72 65 
44 61 74 61
```
Adobe Premiere Pro 2.0 *.prproj* footer: 
```
3C 2F 50 72 65 6D 69 65 72 65 44 61 74 61 3E 0A
```

GoPro Hero HD *.mp4* header: 
```
00 00 00 20 66 74 79 70 61 76 63 31 00 00 00 00 
61 76 63 31 69 73 6F 6D
```
I did not find any common footer between the GoPro files I had. 

Raw MPEG2 *.m2v* video header: 
```
00 00 01 B3 ?? ?? ?? ?? ?? ?? ?? ?? 10 11 11 12
12 12 13 13
```
Raw MPEG2 *.m2v* video footer: 
```
00 00 01 B7
```
IIRC I created these MPEG2 files using [HCEnc 0.28](http://hank315.nl/).

Hope this is useful to someone.

---

