---
title: "convert pdf to video file"
date: 2019-04-27
forum: General Help
---

### Post by satimis on 2019-04-27
Hi all,

Is there an easy way converting pdf to slideshow file, mp4, for upload it to Youtube?

Thanks

satimis

---

### Post by dragonfly41 on 2019-04-27
I suggest starting with [beamer]("https://ctan.org/pkg/beamer").
Then inject your pdf into beamer.

---

### Post by Holger_Gehrke on 2019-04-27
Or you could render the pages of the pdf into images using [convert from ImageMagick]("https://stackoverflow.com/questions/6605006/convert-pdf-to-image-with-high-resolution") or by directly using ghostscript (which is the way convert actually does the conversion) and then [use ffmpeg to create a slideshow]("https://trac.ffmpeg.org/wiki/Slideshow").

Holger

---

### Post by satimis on 2019-04-27
> **Holger_Gehrke said:**
> Or you could render the pages of the pdf into images using [convert from ImageMagick]("https://stackoverflow.com/questions/6605006/convert-pdf-to-image-with-high-resolution") or by directly using ghostscript (which is the way convert actually does the conversion) and then [use ffmpeg to create a slideshow]("https://trac.ffmpeg.org/wiki/Slideshow").

Hi Holger,

Thanks for your advice.

Performed following test:"

1)
Ran pdftk slipping .pdf file to images .jpg

2)
Followed below link to create .avi file
How to create a video from images using FFmpeg?
[https://superuser.com/questions/624567/how-to-create-a-video-from-images-using-ffmpeg](https://superuser.com/questions/624567/how-to-create-a-video-from-images-using-ffmpeg)

3)
Followed Step 3 converting .avi to .mp4 file
[https://itstillworks.com/convert-avi-mp4-linux-5836023.html](https://itstillworks.com/convert-avi-mp4-linux-5836023.html)

4) open .mp4 with Video
It opens the video but unable to play only standing there

5)
Step 4
On Terminal, type the command "mplayer output.mp4"
&#10219; mplayer newtest_01.mp4 ```

MPlayer 1.2.1 (Debian), built with gcc-5.4.0 (C) 2000-2016 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing newtest_01.mp4.
libavformat version 56.40.101 (external)
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG1  595x841  (aspect 1)  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in ./
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 56.60.100 (external)
Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg MPEG-1)
==========================================================================
Audio: no sound
Starting playback...
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 595x841 => 595x841 Planar YV12 
Movie-Aspect is 0.71:1 - prescaling to correct movie aspect.
VO: [vdpau] 595x841 => 596x841 Planar YV12 
V:   0.3   4/  4 ??% ??% ??,?% 0 0 

```

.mp4 file collapses immediately.

Any advice?  Thanks

Regards
satimis

---

### Post by Rubi1200 on 2019-04-27
And this would not do the job for you?
[https://app.pdf2mp4converter.com/pdf2mp4v1.5/](https://app.pdf2mp4converter.com/pdf2mp4v1.5/)

---

### Post by satimis on 2019-04-28
> **Rubi1200 said:**
> And this would not do the job for you?
[https://app.pdf2mp4converter.com/pdf2mp4v1.5/](https://app.pdf2mp4converter.com/pdf2mp4v1.5/)
Hi,

Thanks for your link.

I tried it before starting this thread but failed

After finish -> Download -> Open with Video
```

An error occurred
Stream contains no data
[OK]

```

I haven't made any change to the preset data.

The .mp4 file - 0 bytes, Text

Regards
satimis

---

### Post by Holger_Gehrke on 2019-04-28
Use ghostscript to turn the pdf into a set of jpegs:
```

gs -dNOPAUSE -dBATCH -sDEVICE=jpeg -dDEVICEWIDTHPOINTS=1920 -dDEVICEHEIGHTPOINTS=1080 -dFIXEDMEDIA -sOutputFile=page-%03d.jpg my-file.pdf

```
The DEVICEHEIGHTPOINTS and DEVICEWIDTHPOINTS definitions give the size of the images, the FIXEDMEDIA definition stops gs from overriding those values with the paper size stored in the file. Replace my-file.pdf with the name of your PDF file. The DEVICEHEIGHT should be even, ffmpeg will abort if asked to create mp4 videos with an odd height

Create a Video from the images with ffmpeg
```

ffmpeg -framerate 1/5 -i page-%03d.jpg -c:v libx264 -r 25 out.mp4

```
The -framerate gives the framerate of the inputstream (the set of images), one image every 5 seconds in this case. The -r gives the output framerate.

Holger

---

### Post by satimis on 2019-04-29
> **Holger_Gehrke said:**
> Use ghostscript to turn the pdf into a set of jpegs:
```

gs -dNOPAUSE -dBATCH -sDEVICE=jpeg -dDEVICEWIDTHPOINTS=1920 -dDEVICEHEIGHTPOINTS=1080 -dFIXEDMEDIA -sOutputFile=page-%03d.jpg my-file.pdf

```
The DEVICEHEIGHTPOINTS and DEVICEWIDTHPOINTS definitions give the size of the images, the FIXEDMEDIA definition stops gs from overriding those values with the paper size stored in the file. Replace my-file.pdf with the name of your PDF file. The DEVICEHEIGHT should be even, ffmpeg will abort if asked to create mp4 videos with an odd height

Create a Video from the images with ffmpeg
```

ffmpeg -framerate 1/5 -i page-%03d.jpg -c:v libx264 -r 25 out.mp4

```
The -framerate gives the framerate of the inputstream (the set of images), one image every 5 seconds in this case. The -r gives the output framerate.

Hi Holger,

Your advice works for me.  Thanks

How to center the page in the video?

Please refer to the screenshot attached here.

Regards
satimis

---

### Post by Holger_Gehrke on 2019-04-29
Change the ghostscript call to give a postscript pageoffset operation, like so:
```
gs -dNOPAUSE -dBATCH -sDEVICE=jpeg -dDEVICEWIDTHPOINTS=1920 -dDEVICEHEIGHTPOINTS=1080 -sOutputFile=page-%03d.jpg -c "<</PageOffset [**300** 0]>> setpagedevice " -dFIXEDMEDIA my-file.pdf
```
You can experiment with the value for the horizontal offset (that's the bold 300 in the code) until it looks right.

Holger

---

### Post by satimis on 2019-04-30
> **Holger_Gehrke said:**
> Change the ghostscript call to give a postscript pageoffset operation, like so:
```
gs -dNOPAUSE -dBATCH -sDEVICE=jpeg -dDEVICEWIDTHPOINTS=1920 -dDEVICEHEIGHTPOINTS=1080 -sOutputFile=page-%03d.jpg -c "<</PageOffset [**300** 0]>> setpagedevice " -dFIXEDMEDIA my-file.pdf
```
You can experiment with the value for the horizontal offset (that's the bold 300 in the code) until it looks right.

Hi Holger,

It is better but still not in the center

Edit
===
PageOffset   [750 -100]  is the correct number

Regards
satimis

---

### Post by Holger_Gehrke on 2019-04-30
As I said, experiment with the horizontal offset. No need to run the conversion to video before it looks right, just use your favourite image viewer to check the jpeg-files. If the pdf is big enough that rendering takes some time, you might put a '-sPagelist=<comma-separated list of pages to render>' option in the gs-command to render just a few selected pages. In my experiments 300 looked right, but I was using a lower resolution. Redoing the experiment with HD-resolution I found values between 500 and 700 depending on the content of the pages to be better.

Holger

---

### Post by satimis on 2019-04-30
> **Holger_Gehrke said:**
> As I said, experiment with the horizontal offset. No need to run the conversion to video before it looks right, just use your favourite image viewer to check the jpeg-files. If the pdf is big enough that rendering takes some time, you might put a '-sPagelist=<comma-separated list of pages to render>' option in the gs-command to render just a few selected pages. In my experiments 300 looked right, but I was using a lower resolution. Redoing the experiment with HD-resolution I found values between 500 and 700 depending on the content of the pages to be better.

Hi Holger,

Thanks for your advice.

Performed following test:-

Splitting .pdf to pages/images```

$ convert -density 150 input.pdf -quality 90 output.jpg

```

Then start OpenShot and import all images to it

Export the file as .mp4

The video is more clear then running ffmpeg

Files on Youtube
=============
Running ffmpeg
[https://youtu.be/NxvLWauIciA](https://youtu.be/NxvLWauIciA)

Running OpenShot
[https://youtu.be/I5uHjdBbBEY](https://youtu.be/I5uHjdBbBEY)

Is there anyway to improve the quality of video running ffmpeg ?

Thanks

Regards
satimis

---

