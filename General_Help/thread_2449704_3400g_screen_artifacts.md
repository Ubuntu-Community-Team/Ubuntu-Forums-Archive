---
title: "3400g screen artifacts"
date: 2020-09-01
forum: General Help
---

### Post by goochmcroach on 2020-09-01
Hey guys long time lubuntu user (since 2010) but new to the forum here. 
I recently got a new Ryzen 5 3400g box (i love it) and on lubuntu, as well as manjaro, I get severe graphics artifacts. heres an example from yesterday :
[URL="https://ibb.co/t82bwsx"]https://ibb.co/t82bwsx

This happens within all apps and environments.
[/URL]
Seems to me like this might be a video driver issue? I have no problems in Windows 10, only linux, so I suspect the driver, but I dont know for sure.
If anyone has any advice, I would certainly love to hear it!

Thanks

gooch

---

### Post by goochmcroach on 2020-09-01
heres a fresh one
[https://ibb.co/sVVbdmX](https://ibb.co/sVVbdmX)
i use my phone camera because if I press prtscr the screen refreshes and the artifacts are not captured.

---

### Post by coffeecat on 2020-09-01
> **goochmcroach said:**
> 
Seems to me like this might be a video driver issue? I have no problems in Windows 10, only linux, so I suspect the driver, but I dont know for sure.
If anyone has any advice, I would certainly love to hear it!


My advice would be to post details of your graphics hardware so that people can give relevant advice. :wink:

Also, if you want to include images in your posts, please use the attachment facility to upload them to the forum server, rather than links to off-site hosting sites which many are chary of clicking. Go to the advanced message editor and use the paperclip icon to upload pictures.

Welcome to the forum!

---

### Post by dinkidonk on 2020-09-01
If you have wayland enabled (I think it's default on Lubuntu these days), try to disable it.

---

### Post by goochmcroach on 2020-09-01
Hey guys, thanks for responding. After digging around in ubuntuforums, I found my issue and seems as if I resolved it. I disabled IOMMU in BIOS and so far, no glitching! I will certainly notify if the artifacts return!
Coffeecat : apologies for breach of protocol. Noted. Thanks to you, too dinkidonk. I should have looked here for the solution weeks ago. Thanks!

---

### Post by mastablasta on 2020-09-01
could you give new kernel a try and then report to launchpad bug? supposedly the issue is resolved in newer kernel, however it makes me wonder since you said same thing happens on Manjaro.

---

