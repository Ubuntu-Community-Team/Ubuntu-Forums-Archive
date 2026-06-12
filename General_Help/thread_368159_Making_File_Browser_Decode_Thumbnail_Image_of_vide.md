---
title: "Making File Browser Decode Thumbnail Image of video clips"
date: 2007-02-22
forum: General Help
---

### Post by massong on 2007-02-22
I have a directory of mpg & avi (divx/xvid) files which when I first installed ubuntu I tried to open.  When I went into the directly ubuntu displayed each video file with a nice icon which looks like a reel-to-reel tape. Now,I know if I had the video codecs installed the File Browser would have tried to decode these videos and displayed me a thumbnail image of a still frame from the vdeo for each file.

I installed the video codecs (via automatix2) and when I went back into thie directory it still shows me the reel-to-reel tape icon.

If I look in any of my other video directories the File Browser decodes a frame of video (because the codecs are now installed) and displays a frame of video with each file instead of the default reel-to-reel tape.

My question is.. How do I refresh the first direcory I went into so I can force the File Browser to try to show me an image from each video file instead of the reel-to-reel tape.  

I did try the 'Refresh' button on the file browser but it had no effect.

Thanks!
Gary

---

### Post by CocoAUS on 2007-02-22
From [thad hopkins]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#thumbnails"):

```
rm -rf ~/.thumbnails/normal/*
rm -rf ~/.thumbnails/fail/*
```

Basically, Gnome caches the thumbnails into a folder, so when you want those thumbnails updated, you just need to delete the cache.

Worked for me, although a number of WMV files won't show thumbnails.  Hope that helps.

---

