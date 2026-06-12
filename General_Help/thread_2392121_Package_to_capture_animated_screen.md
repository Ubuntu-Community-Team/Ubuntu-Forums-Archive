---
title: "Package to capture animated screen"
date: 2018-05-17
forum: General Help
---

### Post by satimis on 2018-05-17
Hi all

What will be the easy way to capture an animated screen and save it to local PC as gif.  Which package shall I use?

I have "ScreenShot" installed but it can't save the captured screen as gif file.

Thanks in advance.

Regards
satimis

---

### Post by again? on 2018-05-17
Peek
[https://launchpad.net/~peek-developers/+archive/ubuntu/stable](https://launchpad.net/~peek-developers/+archive/ubuntu/stable)
> Peek makes it easy to create short screencasts of a screen area. It was built for the specific use case of recording screen areas,
 e.g. for easily showing UI features of your own apps or for showing a bug in bug reports. 
With Peek you simply place the Peek window over the area you want to record and press "Record". 
Peek is optimized for generating animated GIFs, but you can also directly record to WebM or MP4 if you prefer.
Peek is not a general purpose screencast app with extended features but rather focuses on the single task of creating small, 
silent screencasts of an area of the screen for creating GIF animations or silent WebM or MP4 videos.  ]

or
simplescreenrecorder can record to other formats with small file size with the right settings.
I can record 20 seconds to mp4 with a filesize less than 1 mb.
simplescreenrecorder is in 17.10 and up repos.

---

### Post by kazakore on 2018-05-17
> **guber2 said:**
> 
simplescreenrecorder can record to other formats with small file size with the right settings.
I can record 20 seconds to mp4 with a filesize less than 1 mb.
simplescreenrecorder is in 17.10 and up repos.

Is that better than RecordMyDesktop, which has been in the repos for quite some time?

---

### Post by again? on 2018-05-17
In my experience, yes.
[http://www.maartenbaert.be/simplescreenrecorder/](http://www.maartenbaert.be/simplescreenrecorder/)

---

### Post by satimis on 2018-05-17
Hi all,

Sorry for not explaining clear on my original posting.

I don't need to record the desktop screen.  What I need is to crop an animated gif image file which is a logo created on online website.  I need to cut the animated gif image to my required size before posting it on a webpage.

Now I found following online website which helps me cutting a gif image;
Crop animated GIF image
[https://ezgif.com/crop/ezgif-5-9ee657db13.gif](https://ezgif.com/crop/ezgif-5-9ee657db13.gif)

But still there is an unresolved problem - how to make the border of the animated gif file, with transparent background, disappeared?

Suggestion would be appreciated.

Regards
satimis

---

### Post by kazakore on 2018-05-17
You can use GIMP to create and edit gifs.

[https://www.gimp.org/tutorials/Simple_Animations/](https://www.gimp.org/tutorials/Simple_Animations/)

---

### Post by SeijiSensei on 2018-05-17
If you import the entire GIF image in the GIMP, it will be converted into a set of layers.  You can edit and resize the entire image, or edit individual frames.

In GIMP, File > Open > point to the file.  Edit > Scale Image to resize.  You need to use File > Export to resave it as an animated gif.  Using File > Save will create a file in GIMP's native .xcf format.

I do this all the time to create [animated avatars](http://www.takinganimeseriously.com/images/avatars/) after grabbing the frames from a video file with ffmpeg.

You've made a couple of postings recently about needing to edit images.  If so, you really need to acquaint yourself with GIMP.  If you work with video, ffmpeg is the Swiss-army-knife of video toolsets

---

### Post by satimis on 2018-05-17
> **SeijiSensei said:**
> If you import the entire GIF image in the GIMP, it will be converted into a set of layers.  You can edit and resize the entire image, or edit individual frames.

In GIMP, File > Open > point to the file.  Edit > Scale Image to resize.  You need to use File > Export to resave it as an animated gif.  Using File > Save will create a file in GIMP's native .xcf format.

I do this all the time to create [animated avatars](http://www.takinganimeseriously.com/images/avatars/) after grabbing the frames from a video file with ffmpeg.

You've made a couple of postings recently about needing to edit images.  If so, you really need to acquaint yourself with GIMP.  If you work with video, ffmpeg is the Swiss-army-knife of video toolsets
Hi,

Thanks for your advice.

I haven't run GIMP for sometimes.  First I ran PhotoShop and then GIMP.  I'll come back.  In my personal opinion GIMP is not a simple tool.  I need a bigger monitor?  I'm now running Dell 24" 2560x1800 monitor.

I use ffmpeg often.  It is a convenient command tool running on terminal .  But it is NOT what-you-see-is-what-you-get which is its disadvantage.

Regards
satimis

---

### Post by monkeybrain20122 on 2018-05-18
[https://askubuntu.com/questions/107726/how-to-create-animated-gif-images-of-a-screencast](https://askubuntu.com/questions/107726/how-to-create-animated-gif-images-of-a-screencast)

[peek]("https://code.launchpad.net/~peek-developers/+archive/ubuntu/stable") sounds like what you are looking for,

---

### Post by SeijiSensei on 2018-05-18
> **satimis said:**
> I haven't run GIMP for sometimes.  First I ran PhotoShop and then GIMP.  I'll come back.  In my personal opinion GIMP is not a simple tool.  I need a bigger monitor?  I'm now running Dell 24" 2560x1800 monitor.
I've used the GIMP on a 19" 4x3 monitor and my current 1080p monitor without any fuss.  GIMP does proliferate windows, though there is now a "[single-window" mode](https://www.gimp.org/release-notes/gimp-2.8.html) that you might find more appealing.

---

### Post by satimis on 2018-05-19
> **SeijiSensei said:**
> I've used the GIMP on a 19" 4x3 monitor and my current 1080p monitor without any fuss.  GIMP does proliferate windows, though there is now a "[single-window" mode](https://www.gimp.org/release-notes/gimp-2.8.html) that you might find more appealing.
Thanks for your advice and link.

I got it;
top menu
-> Windows -> Single-Window Mode

Regards
satimis

---

