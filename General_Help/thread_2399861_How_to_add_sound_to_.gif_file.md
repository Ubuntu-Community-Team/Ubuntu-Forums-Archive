---
title: "How to add sound to .gif file ?"
date: 2018-08-30
forum: General Help
---

### Post by satimis on 2018-08-30
Hi all,

I ran following command converting .mp4 file to .gif file

```

&#10219; ffmpeg -i imput.mp4 -r 10 -f image2pipe -vcodec ppm - | \ 
> convert -delay 5 -loop 0 - output.gif

```

but without sound.

Is there any way adding sound clip to .gif file ?

Command line is preferred.

Thanks

Regards
satimis

---

### Post by Holger_Gehrke on 2018-08-30
To the best of my knowledge there's no way to store sound in a **G**raphics **I**nterchange **F**ormat file. You could put the sound in a separate file and start the sound together with the animation ...

Holger

---

### Post by bizhat on 2018-08-30
Never seen a GIF with sound,  do you have a sample ?

---

### Post by HermanAB on 2018-08-30
That's what mp4 is 4.

---

### Post by satimis on 2018-08-30
> **bizhat said:**
> Never seen a GIF with sound,  do you have a sample ?
Hi,

Before posting I have searched a while on Internet.  Followings are few samples found by me;

Sound GIF - Find & Share on GIPHY
[https://giphy.com/gifs/sound-vybWlRniCXzZC](https://giphy.com/gifs/sound-vybWlRniCXzZC)

GIFs with Sound Mashups
[https://gifsound.com/](https://gifsound.com/)

Funny Gifs With Sound GIFs | Tenor
[https://tenor.com/search/funny-gifs-with-sound-gifs](https://tenor.com/search/funny-gifs-with-sound-gifs)

Regards
satimis

---

### Post by satimis on 2018-08-30
> **Holger_Gehrke said:**
> To the best of my knowledge there's no way to store sound in a **G**raphics **I**nterchange **F**ormat file. You could put the sound in a separate file and start the sound together with the animation ...

Holger
Hi,

Could you shed me some light how to make it.

On browsing the webpage, the .gif file will start automatically and repeat automatically.

Regards
satimis

---

### Post by bizhat on 2018-08-30
Check this

[https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/replace-animated-gifs-with-video/](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/replace-animated-gifs-with-video/)

Many  sites use MP4 instead of gif as it is more optimized. Once your GIF is converted to mp4, it is basically a video format, so you can add  sound to it.

---

### Post by satimis on 2018-08-30
> **HermanAB said:**
> That's what mp4 is 4.
Hi.

It is a short .mp4 file (video) on Youtube which I'll work.  I embed it on the webpage.

Is there a way after starting it will replay automatically unless I stop it manually?

Thanks

Regards
satimis

---

### Post by satimis on 2018-08-30
> **bizhat said:**
> Check this

[https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/replace-animated-gifs-with-video/](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/replace-animated-gifs-with-video/)

Many  sites use MP4 instead of gif as it is more optimized. Once your GIF is converted to mp4, it is basically a video format, so you can add  sound to it.
Hi,

It is a .mp4 file already.  Please see my reply to HermanAB on #8

satimis

---

### Post by bizhat on 2018-08-30
You can download the mp4, put on some othe web sites, then use HTML 5 video player to play the video. Use loop attribute to repeat the video playback.

[https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)

---

### Post by satimis on 2018-08-31
> **bizhat said:**
> You can download the mp4, put on some othe web sites, then use HTML 5 video player to play the video. Use loop attribute to repeat the video playback.

[https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)

Hi,

I'm prepared putting the video on my WordPress website.

It is a short mp4 video captured with video camera.  The original file size is 21MB.  My hosting company doesn't allow uploading file exceeding 1MB to their server.  Therefore I have to run following command reducing the frame size to 1/5 of its original size;```

$ ffmpeg -i input.mp4 -vf scale=iw/5:-1 output.mp4

```

The resultant file size is 952.3kB.  I'm worrying the video frame being too small.  

The best solution is to upload the orginal mp4 video to Youtube and create a link to my webpage. (I have done it many times without problem).  But I have no clue to make it to play automatically when a visitor browses that webpage.  Until it is stopped by the visitor manually.

Regards
satimis

---

### Post by HermanAB on 2018-08-31
Reduce the frame rate.  High frame rates are only needed for fast smooth motion, blinking and lip sync.

Old cartoons run at 7.5 frames per second and that is fast enough for Wiley Coyote and the Road Runner.

Depending on what the video is about, anything from 2 to 10 fps should suffice.

---

### Post by SeijiSensei on 2018-08-31
I'll just mention that I hate websites that autoplay video clips, especially if there's no way to turn off that "feature" permanently.

---

### Post by satimis on 2018-08-31
Hi all,

Now I have the video upload.  Please refers to the attached photo.

Coding```

.....
<a href="http://life.reynoldstocks.com/wp-content/uploads/2018/08/command_transp60.png"><img class="alignleft size-full wp-image-1654" style="border: 0;" src="http://life.reynoldstocks.com/wp-content/uploads/2018/08/command_transp60.png" alt="" width="264" height="83" /></a>

[video width="384" height="216" mp4="http://life.reynoldstocks.com/wp-content/uploads/2018/08/captain5.mp4"][/video]

```

Please advise how to align the description and the video side-by-side?  The description will be in the center height of the video?

Thanks

Regards
satimis

---

### Post by HermanAB on 2018-09-01
Rather than reducing the size so much, reduce the frame rate.  Going from 30 fps to 7.5 fps means the file is 25% of the original size.

The ffmpeg documentation is here: 
[https://www.ffmpeg.org/documentation.html](https://www.ffmpeg.org/documentation.html)

It tells you everything you want to know.

---

