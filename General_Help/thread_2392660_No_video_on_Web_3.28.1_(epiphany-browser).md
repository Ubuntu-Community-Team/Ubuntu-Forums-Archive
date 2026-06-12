---
title: "No video on Web 3.28.1 (epiphany-browser)"
date: 2018-05-23
forum: General Help
---

### Post by Ahunt on 2018-05-23
I am running Lubuntu 18.04 LTs and have installed the Web 3.28.1 web browser (package = epiphany-browser). I do not have Adobe Flash installed (non-free software) and instead rely on HTML5 video. This works fine in other browsers such as Firefox, Chromium, etc, but Web will not play video, such as YouTube, Vimeo, etc. When attempting to play video the audio plays fine, but the video image is missing.

In past versions of Lubuntu, the installation of video codecs from the [ubuntu-restricted-addons]("https://launchpad.net/ubuntu/+source/ubuntu-restricted-addons") resolved video issues, but that package now contains only chromium-codecs-ffmpeg-extra, gstreamer1.0-fluendo-mp3, gstreamer1.0-libav, gstreamer1.0-plugins-ugly and gstreamer1.0-vaapi and testing seems to indicate that this does not allow videos to be played on Web 3.28.1.

The [HTML5 test]("http://html5test.com/") shows under "Video": 

video element Yes &#10004;
Subtitles Yes &#10004;
Audio track selection Yes &#10004;
Video track selection Yes &#10004;
Poster images Yes &#10004;
Codec detection Yes &#10004;

Video codecs
MPEG-4 ASP support No &#10008;
H.264 support No &#10008;
H.265 support No &#10008;
Ogg Theora support Yes &#10004;
WebM with VP8 support Yes &#10004;
WebM with VP9 support Yes &#10004;

Any solutions?

---

### Post by kerry_s on 2018-05-23
try:
```
sudo apt -y install libdvdcss2 ffmpeg
sudo dpkg-reconfigure libdvd-pkg
```

---

### Post by Ahunt on 2018-05-24
Thank you for the suggestion. That all installed and ran just find, but it didn't solve the issue, still no video on Web 3.28.1.

---

### Post by kerry_s on 2018-05-24
well, you know web does not have none of the mse type html5. [https://www.youtube.com/html5](https://www.youtube.com/html5)

some sites say, there html5, but they don't say you need the full html5 support. also there's that drm thing.

web is best used for web browsing, for media/videos your best bet is a full featured browser.

---

### Post by Ahunt on 2018-05-24
Well the frustrating thing is that previous versions of Web worked fine with YouTube, etc with HTML5 video. Something has changed since then. I may have to appeal to the Epiphany dev list unless anyone else has some ideas?

---

### Post by Ahunt on 2018-05-25
Since no solutions were found here, I posted this issue on the [Web dev mailing list]("https://mail.gnome.org/archives/epiphany-list/2018-May/thread.html") and found a solution there. To enable video on Web 3.28.1 you need to: 

```
sudo apt install gstreamer1.0-gl gstreamer1.0-libav
```

---

