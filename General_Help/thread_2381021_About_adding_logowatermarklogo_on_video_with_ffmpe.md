---
title: "About adding logo/watermarklogo on video with ffmpeg command line"
date: 2017-12-25
forum: General Help
---

### Post by satimis on 2017-12-25
Hi all,

I found following commands on Internet

Top left corner```

ffmpeg –i inputvideo.mp4 -vf "movie=watermarklogo.png [watermark]; [in][watermark] overlay=10:10 [out]" outputvideo.mp4

```

Top right corner```

ffmpeg –i inputvideo.mp4 -vf "movie=watermarklogo.png [watermark]; [in][watermark] overlay=main_w-overlay_w-10:10 [out]" outputvideo.mp4

```

Bottom left corner```

ffmpeg –i inputvideo.mp4 -vf "movie=watermarklogo.png [watermark]; [in][watermark] overlay=10:main_h-overlay_h-10 [out]" outputvideo.mp4

```

Bottom right corner```

ffmpeg –i inputvideo.mp4 -vf "movie=watermarklogo.png [watermark]; [in][watermark] overlay=(main_w-overlay_w-10)/2:(main_h-overlay_h-10)/2 [out]" outputvideo.mp4

```

How about add the logo/watermarklogo on other location?  How to set the coordinate?

Please advise.  Thanks

Regards
satimis

---

### Post by HermanAB on 2017-12-25
Best is to read the manual:
[https://www.ffmpeg.org/documentation.html](https://www.ffmpeg.org/documentation.html)

There are not many people who would want to do what you want, so you may never get any real help to such a question.

---

