---
title: "How do I install ffmpeg with Synaptic ?"
date: 2015-06-04
forum: General Help
---

### Post by gr8 on 2015-06-04
I installed ffmpeg and winff utilizing the Ubuntu Software Center (USC). I then got some libav errors. No problem I just installed the libav stuff that USC said I was missing. I installed libav-56, libav-extras, and a bunch of other libav-items. That didn't work. Still got the same errors.

I might as well just delete all this stuff from the Ubuntu Software Center and install fresh using Synaptic. I guess Synaptic is better. How do I install ffmpeg properly from Synaptic, and what else do I need to install with it. I guess they're called dependencies (libav, etc).

---

### Post by QDR06VV9 on 2015-06-04
Hi gr8 This is for 14.04
Enter the code below one line at a time.
```
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get dist-upgrade


```

And Then
```
sudo apt-get install ffmpeg
```
More Info for that PPA here [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
Regards

---

### Post by gr8 on 2015-06-04
Isn't this the method to install with the terminal? I want to do it through Synaptic because I've heard it keeps everything tidy (ie it downloads all dependencies, and does everything you need). Am I correct? If so how do I do everything through Synaptic? Thank you.

---

### Post by kerry_s on 2015-06-04
the terminal does dependences to. use the terminal to add the ppa & if you wish you can use synaptic for install.

---

### Post by QIII on 2015-06-04
There is a long and sordid story about the war between the libav/avconv fork faction and the ffmpeg faction.

Debian has removed ffmpeg from upstream.  Suffice it to say that Ubuntu no longer ships ffmpeg.  You'll have to use a PPA if you want it.

Synaptic is a front end for apt, so either do it from the terminal or add the PPA and use Synaptic.

---

### Post by FakeOutdoorsman on 2015-06-05
ffmpeg from FFmpeg returned to Ubuntu in 15.04.

---

### Post by QIII on 2015-06-05
Good to hear!

---

