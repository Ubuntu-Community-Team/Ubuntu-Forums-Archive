---
title: "How to convert jpg file into webp file in kubuntu 18?"
date: 2020-06-26
forum: General Help
---

### Post by petrogromovo on 2020-06-26
Hello,
What with can I to convert jpg file into webp file in kubuntu 18?
I tried to make it in gimp, but failed...

Thanks!

---

### Post by Holger_Gehrke on 2020-06-26
As with many image format conversion questions, the answer is ImageMagick. A simple 'convert oldfile.whatever-other-image-format newfile.webp' will do the trick. Small warning: as far as ImageMagick is concerned, format conversion is just the tip of the iceberg. It's sometimes called the Photoshop of command line graphics tools, so mastering it's many capabilities can take years.

Holger

---

### Post by petrogromovo on 2020-06-26
Thanks for your feedback!
if [COLOR=#000000]Photoshop of command line graphics tools works under kubuntu ?
Are the some online services for image [/COLOR][COLOR=#000000] type [/COLOR][COLOR=#000000]convertion ?[/COLOR]

---

### Post by Yellow Pasque on 2020-06-26
Some alternatives are cwebp and ffmpeg:
```
sudo apt-get install webp
cwebp input.jpg -o output.webp

ffmpeg -i input.jpg -c:v libwebp output.webp
```

Documentation of options:
[https://developers.google.com/speed/webp/docs/cwebp](https://developers.google.com/speed/webp/docs/cwebp)
[https://ffmpeg.org/ffmpeg-codecs.html#libwebp](https://ffmpeg.org/ffmpeg-codecs.html#libwebp)

---

### Post by Holger_Gehrke on 2020-06-26
> **petrogromovo said:**
> 
if [COLOR=#000000]Photoshop of command line graphics tools works under kubuntu ?
[/COLOR]

'ImageMagick is sometimes called the Photoshop of command line graphics tools' means it's being compared to Photoshop in terms of capabilities and steepness of the learning curve if you want to use all of it. Since it's a set of command line tools it works on any Linux system including all the flavours of Ubuntu. It also works on servers which don't have any GUI at all, a lot of server side image processing is done using ImageMagick (or the libraries which sit at the core of these tools, libMagickCore and libMagickWand). If there are online services for doing this conversion, then they are probably using ImageMagick to do the actual work. It's probably already installed on a KUbuntu system, since 'apt show imagemagick' lists 'kubuntu-desktop' as one of the tasks that the package is a part of. If it's not installed on your system, then a simple 'sudo apt install imagemagick' will download and install it.

Holger

---

