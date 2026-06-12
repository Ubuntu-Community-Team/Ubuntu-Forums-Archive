---
title: "HBOGO on Firefox - No video, only audio"
date: 2016-05-21
forum: General Help
---

### Post by Owen_Murphy on 2016-05-21
Hello,
I am trying to get HBOGo to work on Firefox.  I understand that HBOGO uses DRM software to verify your identity, which requires something called HAL.  I have installed HAL from the mjblenner repository:
```
sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal

```
I have also installed and enabled Pipelight using instructions from the following forum post:
[http://ubuntuforums.org/showthread.php?t=2274467](http://ubuntuforums.org/showthread.php?t=2274467)
```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update
sudo apt-get remove flashplugin-installer
sudo pipelight-plugin --enable flash
sudo pipelight-plugin --enable widevine
sudo pipelight-plugin --enable silverlight
sudo pipelight-plugin --update
sudo pipelight-plugin --create-mozilla-plugins
```


Previously (several months ago) I had been able to play HBOGO shows without any issue, but recently I've been having issues.  At first the show would play, but it would be extremely glitchy.  The video wouldn't sync up to the audio and the video track it self seemed "jerky" (it would pause, then jump forward over and over again).  

Last night I tried again to get it to work, and now there is no video whatsoever - only audio.  I have since removed any packages I've installed, but there is still no video.

Sidenote: I am able to play the adobe DRM self test video perfectly fine:
[COLOR=#333333][FONT=adobe-clean]http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html
[/FONT][/COLOR]with:[COLOR=#333333][FONT=adobe-clean]http://drmtest2.adobe.com:8080/Content/anonymous.f4v

[/FONT][/COLOR]Any ideas?

Thanks,
Owen

---

### Post by Owen_Murphy on 2016-05-24
Anything...?  I need to watch Game of Thrones...

---

### Post by Owen_Murphy on 2016-05-26
Please help. I need to find out what Hodor means.

---

