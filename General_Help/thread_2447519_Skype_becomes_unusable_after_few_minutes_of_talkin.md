---
title: "Skype becomes unusable after few minutes of talking"
date: 2020-07-20
forum: General Help
---

### Post by foxy123 on 2020-07-20
I've got Skype installed on an old laptop (some Lenovo model from 2010) on Ubuntu 16.04. The laptop is not physically with me so all I can do is only through Teamviewer. Skype became pretty unusable on the laptop. After a few minutes of normal conversation, it slows down immensely, both video and audio. I looked at the CPU usage and it's around 60-70%. I understand that the laptop is pretty old and the OS is outdated, but unfortunately, it's all I've got now. I wonder if it's possible to do anything about it? If I had a physical access to the laptop, I would replace Ubuntu with something lighter like the latest version of Lubuntu or something. Not sure if it would help with Skype though. In any case, any advice will be appreciated. Oh, another thing. I had the same issue with the laptop some years ago, but I found on the net that the problem might be with CPU throttling. There was a solution there how to prevent it. It worked, and Skype had stopped slowing down. Though I was always a bit uneasy with the fact that CPU had a higher load than it should.

---

### Post by CatKiller on 2020-07-20
It seems likely that what you're missing is hardware-accelerated encode/decode of the video stream. I haven't used Skype in a long time, and didn't use it for video when I did, but that's what I'd look at first.

---

### Post by foxy123 on 2020-07-20
> **CatKiller said:**
> It seems likely that what you're missing is hardware-accelerated encode/decode of the video stream. I haven't used Skype in a long time, and didn't use it for video when I did, but that's what I'd look at first.

Thanks a lot. Any way to check it?

---

### Post by CatKiller on 2020-07-20
No idea, sorry. Intel uses VA-API, Nvidia uses nvenc/nvdec or VDPAU, and I don't know what AMD uses. I have no idea which, if any, Skype can make use of.

---

