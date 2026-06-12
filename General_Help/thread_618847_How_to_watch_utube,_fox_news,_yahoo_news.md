---
title: "How to watch utube, fox news, yahoo news"
date: 2007-11-20
forum: General Help
---

### Post by LinuxHawk on 2007-11-20
Is there a plug in I am missing to be able to watch the videos on Fox News, or Yahoo News, and some Utube videos.

When I TRY TO WATCH NEWS CLIP VIDEOS i JUST GET A BLACK BOX WHERE the video would be playing.

I am using Gutsy Kubuntu with Firefox for the browser.

I get nothing from the browser that asks if I want to download any plug ins.

Am I out of luck with Ubuntu?

Thanks in advance...

---

### Post by ice60 on 2007-11-20
try searching for flash.
```
apt-cache search flash
```
if you see it in the results you can install it like this
```
sudo apt-get install <the name of the flash program you found>
```

---

### Post by LinuxHawk on 2007-11-20
Thanks for the response and the code.
I installed several, and it said they were already installed.

I closed down Firefox, then reopened it, but still no video from many places as common as fox news.

Any other things I should be doing?

Thanks again in advance...

---

### Post by doctorgreg on 2007-11-20
This is what I have installed for flash. Macromedia Flash plugin, GStreamer ffmpeg video plugin, Ubuntu restricted extras, and Movie Player.  All of these should be available in synaptics or add remove. Hope it helps you out.

---

### Post by doctorgreg on 2007-11-20
oh yeah i also have adobe flashplugin-nonfree.  Don't bother using gnash.  If you have it installed get rid of it.

---

