---
title: "Can .pdf be converted direct to mp4"
date: 2023-01-03
forum: General Help
---

### Post by satimis on 2023-01-03
Hi all,

Ubuntu 22.04

I wonder whether there is a way converting .pdf direct to video.mp4?  

The .pdf file is created on *jpg files.  I can create slideshow on *jpg and export it as .mp4 file on OpenShot or similar software

I wonder whether there is a lazy way converting .pdf file direct to mp4 ?

Can ImageMagick or ffmpeg do the job?

Please advise.  Thanks

Regards

---

### Post by TheFu on 2023-01-03
Open the PDF in full screen mode and record your screen to whatever format you like at the pace you like.
If you want to change the page every 15 seconds, you can use something like 'xdotool' to send the pgdn key every 15 seconds to that program.

If you are adding audio, just manually control the paging after you record the audio.

BTW, you probably want to only capture 1fps to keep the mp4 size as small as possible.  Perhaps even 1 frame every 2-5 seconds would be enough? mp4 containers aren't some magic tool. It is mostly about the fps, video codec and resolution that make for large files.

Heck, you could just use a screen capture tool to grab an image file while watching the PDF, then feed those into your jpg/png/gif --> mp4 conversion.

---

### Post by #&amp;thj^% on 2023-01-03
> **satimis said:**
> 

Can ImageMagick or ffmpeg do the job?

Please advise.  Thanks

Regards

[https://ostechnix.com/create-video-pdf-files-linux/](https://ostechnix.com/create-video-pdf-files-linux/)

---

### Post by satimis on 2023-01-03
Hi all,

Thanks for your advice.

What I'm trying to do is to import the .pdf file on OpenShot or similar video editor to create a slideshow.  Then I can start editing there, such as adding background music, narration, subtitles etc.  There are >60 pages (photos) on the .pdf file.  I still retain all photos but it will take quite sometime to import them to OpenShot, one by one, and add them to the time-line.

I'm interested learning something completely new to me.  How to do the job to create a slideshow on commands running ImageMagick which is running on my PC ?

I'll try the suggestion on 1fallen's link later.  Convert .pdf to .mp4 file and then import the later to OpenShot starting editing.  I'll come back after testing.

Regards

---

### Post by satimis on 2023-01-03
> **TheFu said:**
> Open the PDF in full screen mode and record your screen to whatever format you like at the pace you like.
If you want to change the page every 15 seconds, you can use something like 'xdotool' to send the pgdn key every 15 seconds to that program.

If you are adding audio, just manually control the paging after you record the audio.
Thanks for your advice.

Could you pls explain in more detail?  Pointer would be appreciated.

Thanks

Regards

---

### Post by TheFu on 2023-01-03
> **satimis said:**
> Thanks for your advice.

Could you pls explain in more detail?  Pointer would be appreciated.

Use any tool you like to record the screen.  SimpleScreenRecorder, ffmpeg, OSB, there must be 20 of them.  If you are using Wayland, there are other tools, I'm certain. Last time I checked, only the Gnome people made one that actually worked.

[https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop)

---

### Post by satimis on 2023-01-04
> **1fallen said:**
> [https://ostechnix.com/create-video-pdf-files-linux/](https://ostechnix.com/create-video-pdf-files-linux/)
Hu 1fallen,

Performed following test according to your link;
(After installing ffmpeg and imagemagick, convert your PDF file image format such as PNG or JPG like below.)

Create a folder, Testing
Copy AAA.pdf file on Testing folder

On Terminal;
cd Testing
$ convert -density AAA.pdf picture.png

It just hanged there without progressing.

$ which ffmpeg
/usr/bin/ffmpeg

$ which convert
/usr/bin/convert

Regards


[B][COLOR="#FF0000"]Edit
==[/COLOR][/B]
It is working but very slow.  Finally only 8 pictures generated with following warning popup
```

convert-im6.q16: cache resources exhausted `/tmp/magick-n5Ms7Zl7x2q6EsGKUsxc_ABAmkZc9kOi10' @ error/cache.c/OpenPixelCache/4095.

```
There are 30 pages(i.e. 30 pictures) on the .pdf file

On Terminal run;
$ sudo nano /etc/ImageMagick-6/policy.xml

On the line:  <policy domain="resource" name="disk" value="1GiB"/
**[COLOR="#FF0000"]change 1GiB to 16GiB[/COLOR]**

Save and exit.  Start again

But still the same with only 8 pictures generated

Warning:```

convert-im6.q16: cache resources exhausted `/tmp/magick-zaevVGagkbjIBqZPIdyPZUD1W4uhb06e10' @ error/cache.c/OpenPixelCache/4095.

```

Any suggestion?  Thanks

[B][COLOR="#FF0000"]Edit-2
====[/COLOR][/B]

Following command works;```

$ convert -density 150 -quality 70 AAA.pdf picture.jpg

```
30 pictures generated
picture-0.jpg
picture-1.jpg
....
....
picture-28.jpg
picture-29.jpg

Again on Terminal run;
$ ffmpeg -r 1/10 -i picture-%01d.jpg -c:v libx264 -r 30 -pix_fmt yuv420p video.mp4

Finally a video is created but it takes long time to complete with following warning pop;
```

deprecated pixel format used, make sure you did set range correctly

```

I just ignore the warning.

However the quality of the video is not good.  It would be better to do it on Open Source editor, such as OpenShot

---

### Post by satimis on 2023-01-04
> **TheFu said:**
> Use any tool you like to record the screen.  SimpleScreenRecorder, ffmpeg, OSB, there must be 20 of them.  If you are using Wayland, there are other tools, I'm certain. Last time I checked, only the Gnome people made one that actually worked.

[https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop)
Yes, I have SimpleScreenRecorder running.

But starting the .pdf file, it won't run automatically.

Regards

---

