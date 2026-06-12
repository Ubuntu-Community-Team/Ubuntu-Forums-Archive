---
title: "Software Updater"
date: 2015-06-09
forum: General Help
---

### Post by dreamquartz on 2015-06-09
Received:
Security updates
Extra ffmpeg codecs for Chromium Browser.

I do NOT use Chromium Browser.
So why do I get it?

John

---

### Post by deadflowr on 2015-06-09
They should be part of the ubuntu-restricted-extras packages...

---

### Post by vasa1 on 2015-06-09
> **deadflowr said:**
> They should be part of the ubuntu-restricted-extras packages...

And you can see that here:```
07:16 AM ~ $ apt-cache rdepends chromium-codecs-ffmpeg-extra
chromium-codecs-ffmpeg-extra
Reverse Depends:
  chromium-codecs-ffmpeg-extra:i386
  chromium-codecs-ffmpeg:i386
  chromium-codecs-ffmpeg:i386
  chromium-codecs-ffmpeg-extra-dbg
  chromium-codecs-ffmpeg
  chromium-codecs-ffmpeg
 |chromium-browser
  chromium-codecs-ffmpeg-extra:i386
  chromium-codecs-ffmpeg:i386
  chromium-codecs-ffmpeg:i386
**  ubuntu-restricted-addons**
  kubuntu-restricted-addons
  chromium-codecs-ffmpeg-extra-dbg
  chromium-codecs-ffmpeg
  chromium-codecs-ffmpeg
 |chromium-browser
07:16 AM ~ $ 

```

---

### Post by dreamquartz on 2015-06-10
Thanks

Dream

---

