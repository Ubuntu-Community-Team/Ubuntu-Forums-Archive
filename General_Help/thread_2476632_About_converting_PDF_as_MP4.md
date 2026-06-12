---
title: "About converting PDF as MP4"
date: 2022-07-01
forum: General Help
---

### Post by satimis on 2022-07-01
Hi all,

I have PDF files combining from photos.

ffmpeg can convert PDF to mp4 video.  There many links introducing how to make it.   Also there are many FREE online solution.

But I can't resolve how can photos be converted as video?  Whether it just converts the PDF as slideshow?

Please shed me some light.  Thanks

Regards

---

### Post by #&amp;thj^% on 2022-07-01
> **satimis said:**
>  Whether it just converts the PDF as slideshow?

Please shed me some light.  Thanks

Regards
Yep you are correct.

I'll use this as an example: you can use ffmpeg format specifiers to indicate the images that FFmpeg should use:
```
 ffmpeg -framerate 1 -i happy%d.jpg -c:v libx264 -r 30 output.mp4
```

The above command takes an input of images, -i happy%d.jpg. This will search for the image with the lowest digit and sets that as the starting image. It will then increment that number by one and if the image exists, it will be added to the sequence. You can specify the start image yourself with -start_number n.

I  use" -framerate 1" to define how fast the pictures are read in, in this case, 1 picture per second. Omitting the framerate will default to a framerate of 25.

-r 30 is the framerate of the output video. Again, if we didn't define it, it would default to 25.

The "-c:v libx264" specifies the codec to use to encode the video. x264 is a library used for encoding video streams into the H.264/MPEG-4 AVC compression format.
Here is what it would look like: [https://d1uej6xx5jo4cd.cloudfront.net/ffmpeg-slideshow.mp4](https://d1uej6xx5jo4cd.cloudfront.net/ffmpeg-slideshow.mp4)

---

### Post by satimis on 2022-07-01
> **1fallen said:**
> Yep you are correct.

I'll use this as an example: you can use ffmpeg format specifiers to indicate the images that FFmpeg should use:
```
 ffmpeg -framerate 1 -i happy%d.jpg -c:v libx264 -r 30 output.mp4
```

The above command takes an input of images, -i happy%d.jpg. This will search for the image with the lowest digit and sets that as the starting image. It will then increment that number by one and if the image exists, it will be added to the sequence. You can specify the start image yourself with -start_number n.

I  use" -framerate 1" to define how fast the pictures are read in, in this case, 1 picture per second. Omitting the framerate will default to a framerate of 25.

-r 30 is the framerate of the output video. Again, if we didn't define it, it would default to 25.

The "-c:v libx264" specifies the codec to use to encode the video. x264 is a library used for encoding video streams into the H.264/MPEG-4 AVC compression format.
Here is what it would look like: [https://d1uej6xx5jo4cd.cloudfront.net/ffmpeg-slideshow.mp4](https://d1uej6xx5jo4cd.cloudfront.net/ffmpeg-slideshow.mp4)

Thanks for your advice.

Half hour ago on Internet browsing I found following links;

Create A Video From PDF Files In Linux
[https://ostechnix.com/create-video-pdf-files-linux/](https://ostechnix.com/create-video-pdf-files-linux/)

PDF to MP4 online converter
[https://www.coolutils.com/online/PDF-to-MP4](https://www.coolutils.com/online/PDF-to-MP4)

How to convert PDF to MP4
[https://products.aspose.app/pdf/conversion/pdf-to-mp4](https://products.aspose.app/pdf/conversion/pdf-to-mp4)

etc.

What will be the advantage?  

How to add background music, narraction, subtilles. fade in/fade out etc. ?  In the past I have done a lot, creating slideshows on photo editing software, such as OpenShot, Filmora, Shotcut etc.

My idea is whether there is a way in the other way round, converting mp4 to PDF.  What about the animation?

Thanks

Regards

---

### Post by #&amp;thj^% on 2022-07-01
> **satimis said:**
> 
What will be the advantage?  

I'm not sure I only use the method I've shown, I guess you could try them all to see the best out come. :)
> **satimis said:**
> 

How to add background music, narraction, subtilles. fade in/fade out etc. ?  In the past I have done a lot, creating slideshows on photo editing software, such as OpenShot, Filmora, Shotcut etc.


You can make your video slideshow more interesting by adding an audio track to it:

```
$ ffmpeg -framerate 1 -pattern_type glob -i '*.jpg' -i freeflow.mp3 \
  -shortest -c:v libx264 -r 30 -pix_fmt yuv420p output6.mp4
```

The above adds a second input file with** -i freeflow.mp3** which is an audio file.

The** -shortes**t option sets the length of the output video to be the shortest length of the two input files. If the audio is longer than the slideshow.
As for reversing back, just save a copy of the original that won't be touched is my advise.
Oh the Glob part might be useful as well,>>>Using a glob pattern

You can specify the input images to be used in the video with a glob pattern. The pattern *.jpg used  will select all files with names ending in .jpg from the current directory. The matching files will be sorted according to LC_COLLATE. This is useful if you have images named sequentially, but not necessarily in numerical sequential order.

---

### Post by satimis on 2022-07-01
> **1fallen said:**
> Yep you are correct.

I'll use this as an example: you can use ffmpeg format specifiers to indicate the images that FFmpeg should use:
```
 ffmpeg -framerate 1 -i happy%d.jpg -c:v libx264 -r 30 output.mp4
```

The above command takes an input of images, -i happy%d.jpg. This will search for the image with the lowest digit and sets that as the starting image. It will then increment that number by one and if the image exists, it will be added to the sequence. You can specify the start image yourself with -start_number n.

I  use" -framerate 1" to define how fast the pictures are read in, in this case, 1 picture per second. Omitting the framerate will default to a framerate of 25.

-r 30 is the framerate of the output video. Again, if we didn't define it, it would default to 25.

The "-c:v libx264" specifies the codec to use to encode the video. x264 is a library used for encoding video streams into the H.264/MPEG-4 AVC compression format.
Here is what it would look like: [https://d1uej6xx5jo4cd.cloudfront.net/ffmpeg-slideshow.mp4](https://d1uej6xx5jo4cd.cloudfront.net/ffmpeg-slideshow.mp4)
Performed following test;

The PDF file was created on *.jpg and all *.jpg files are in the JPG-directory/folder.

Change to JPG-directory/folder and run your command;
$ ffmpeg -framerate 1 -i happy%d.jpg -c:v libx264 -r 30 output.mp4```

....
.... 
enable-frei0r --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libaribb24 --enable-liblensfun --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc
  libavutil      56. 31.100 / 56. 31.100
  libavcodec     58. 54.100 / 58. 54.100
  libavformat    58. 29.100 / 58. 29.100
  libavdevice    58.  8.100 / 58.  8.100
  libavfilter     7. 57.100 /  7. 57.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  5.100 /  5.  5.100
  libswresample   3.  5.100 /  3.  5.100
  libpostproc    55.  5.100 / 55.  5.100
[image2 @ 0x55ee76ccd780] Could find no file with path 'happy%d.jpg' and index in the range 0-4
happy%d.jpg: No such file or directory

```

What shall I replace "happy" with?  Please see attached screenshot

Thanks

Regards

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]

Following command works for me;```

$ ffmpeg -framerate 1 -pattern_type glob -i '*.jpg' -c:v libx264 combine.mp4

```

But some photos distorted.  Pls refer to attached screeshot

---

