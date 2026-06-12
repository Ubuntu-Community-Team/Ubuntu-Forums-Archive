---
title: "Best Acer Revo 3610 config suggestion for flash streaming (i.e. from CWTV)?"
date: 2017-05-16
forum: General Help
---

### Post by nckhrs on 2017-05-16
Dear All,

I have been searching for how to configure Acer Revo 3610 with Ubuntu/Lubuntu/Xubuntu to be able to watch flash streaming smoothly (i.e. from CWTV website).

I found a lot of info from many many threads, and I tried many different things (tried Lubuntu and Xubuntu, older version and newer version, various flash player, enabling VDPAU, etc.) and to make it short, I found that only Ubuntu works in regards to HDMI sound. I got good result with Youtube with Ubuntu 12.04, however, I am unable to update to the latest Flash Plugin even though I updated the Firefox to ver. 52 (the latest for 12.04 I supposed). And when I forced to run the flash, I still got laggy video. With Ubuntu 14.04.5 I can get the latest Firefix and flash plugin, but still, laggy. And Youtube is worse compared to 12.04.

I found this thread, there are some similar open questions on the last page but unfortunately it's closed already.
[https://ubuntuforums.org/showthread.php?t=1379320&page=7](https://ubuntuforums.org/showthread.php?t=1379320&page=7)

A lot of info I found it how to configure Revo 3610 to play content. But what I need is just to play flash streaming from browser.
Is the hardware too old for it? Should I just go with Roku?

I have spent hours and days to find the answer, I would really appreciate if somebody can shed some light.

Thank you all.

---

### Post by gordintoronto on 2017-05-17
I wouldn't mess around with old versions; I would go with 16.04 or 17.04 (which will have to be updated around the end of the year) of Xubuntu, Mate or Lubuntu. Then I would install the proprietary driver for the Nvidia Ion, which is the same as the GeForce 9400 GT. Then I would install Chrome, and use it for streaming.

What is the resolution of the videos from CWTV? How fast is your Internet connection? That combination might account for most of your problems.

---

### Post by nckhrs on 2017-05-17
> **gordintoronto said:**
> I wouldn't mess around with old versions; I would go with 16.04 or 17.04 (which will have to be updated around the end of the year) of Xubuntu, Mate or Lubuntu. Then I would install the proprietary driver for the Nvidia Ion, which is the same as the GeForce 9400 GT. Then I would install Chrome, and use it for streaming.

What is the resolution of the videos from CWTV? How fast is your Internet connection? That combination might account for most of your problems.

Thanks for your answer.
I tried installing Lubuntu 16.04, and it won't even boot from USB. I thought it must be the HW is too old.
Maybe I should try Ubuntu 16.04 and see.

I don't know the resolution. It requires flash when I watch it over web browser and provide selection of baudrate.
If I remember correctly, there are 4 or 5 baudrate options: "Auto, 2160 kbps, 1240 kbps, 640 kbps, etc."

I got a feeling the flash player is resource hungry.

My internet connection is 100 Mbps, Acer Revo 3610 is Wireless G only.
But I can stream ok with my laptop (also running on Wireless G), so I think internet connection is ok. Or it is not?

I will try your suggestion if I can install Ubuntu 16.04 on it.
Otherwise, I was thinking, would it work to try to install Kodi and stream CWTV from it (to avoid resource hungry flash player)?

Thanks a lot.

---

