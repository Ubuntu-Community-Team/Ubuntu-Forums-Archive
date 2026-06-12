---
title: "Compressing MOV File"
date: 2017-02-20
forum: General Help
---

### Post by daniell59 on 2017-02-20
My camera takes videos in mov. I would like to compress them so I can email them. Is there a program available in Linux that will enable me to do so?

Ubuntu 14.04 32

Thanks in advance.

---

### Post by yancek on 2017-02-20
One option is Handbrake which should be in the repositories of 14.04.  Just open the Software Center and type 'handbrake' in the serch box and when it is found, click Install.  There are several other options as other will likely post about.

---

### Post by howefield on 2017-02-20
I'd think you'd be looking at transcoding the video rather than a simple compression of the file.

Something like Handbrake which has some preset values that might give you something of the file size that you need.

How large are the files ?

---

### Post by daniell59 on 2017-02-20
> **howefield said:**
> I'd think you'd be looking at transcoding the video rather than a simple compression of the file.

Something like Handbrake which has some preset values that might give you something of the file size that you need.

How large are the files ?

The first one is about 53 MB.
Larger ones to follow.

---

### Post by howefield on 2017-02-20
> **daniell59 said:**
> The first one is about 53 MB. Larger ones to follow.

Long before ownCloud came along I used to use a service called "yousendit" (now morphed into something else) - upload a large file and share the link for the recipient to download. There are a ton of these types of file sharing options. The benefit being that the recipient gets the lossless file, the downside being that you are essentially putting your files on a third parties computer.

Gmail has a 25MB file size limit on email but you can get around this limit by using Google Drive, I'm sure other providers, eg Onedrive have similar ways to email large files.

Only mention the above because it is (probably) much easier than transcoding a bunch of files.

---

### Post by daniell59 on 2017-02-20
> **howefield said:**
> Long before ownCloud came along I used to use a service called "yousendit" (now morphed into something else) - upload a large file and share the link for the recipient to download. There are a ton of these types of file sharing options. The benefit being that the recipient gets the lossless file, the downside being that you are essentially putting your files on a third parties computer.

Gmail has a 25MB file size limit on email but you can get around this limit by using Google Drive, I'm sure other providers, eg Onedrive have similar ways to email large files.

Only mention the above because it is (probably) much easier than transcoding a bunch of files.

Much thanks for your informative replies.

---

### Post by HermanAB on 2017-02-20
You cannot really compress a video file, since it is already compressed.

What you need to do is shorten it so it only contains the interesting bit and you could also transcode it to a different resolution or expand and recompress it with a different codec.  All of which will cause a loss of quality.

---

### Post by SeijiSensei on 2017-02-20
I recently re-encoded some large .mov files in QuickTime to Windows Media with great success using ffmpeg:

```
ffmpeg -i input.mov -vcodec wmv3 -acodec aac -strict -2 output.mp4
```

This reduced a 2.8 GB .mov file to a 31 MB .mp4.  Still looks very good.  There are a few screen tears when the camera was panned over complex geometric shapes, but that was it.  (This video is a collection of artworks.)

I chose WMV3 over something like H.264 because WMV3 is supported on a wide number of platforms and devices.

---

### Post by daniell59 on 2017-02-20
My other camera shoots amazingly small AVI files. It has two settings. One for standard AVI files the other for compressed AVI files.

---

