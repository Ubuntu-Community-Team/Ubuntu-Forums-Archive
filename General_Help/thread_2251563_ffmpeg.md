---
title: "ffmpeg"
date: 2014-11-04
forum: General Help
---

### Post by Pedroski55 on 2014-11-04
Where is the best plaxe to get ffmpeg for Ubu 14.04?

I want to run an mp4 video file and an audio m4a file which I got from youtube together, the video is not much fun without the audio! (Leslie Grace, Will you still love me tomorrow)

---

### Post by Doug S on 2014-11-05
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2249092").

---

### Post by Bucky Ball on 2014-11-05
Go to the Software Centre and install it? Or install ubuntu-restricted-extras. Think that drags it, and a bunch of other codecs and things, in.

---

### Post by monkeybrain20122 on 2014-11-05
There are two ppas that provide up to date real ffmpeg (not avconv)  for Ubuntu 14.04 
Either
[https://launchpad.net/~samrog131/+archive/ubuntu/ppa](https://launchpad.net/~samrog131/+archive/ubuntu/ppa)
or
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

---

### Post by stalkingwolf on 2014-11-05
it is available in synaptic package manager

---

### Post by Bucky Ball on 2014-11-05
Yup. That's what I mentioned before. Software Centre means it is available in Synaptics. Just install. See [HERE]("http://ubuntuforums.org/showthread.php?t=2251563&p=13160289&viewfull=1#post13160289").

---

### Post by Doug S on 2014-11-05
For my part of this thread, I was of the understanding that, for Ubuntu 14.04, ffmpeg is not available as a standard package. I couldn't find it looking on [the package web page]("http://packages.ubuntu.com/"), but could for 12.04.
So, I found the other thread which mentions how to do it for 14.04, one of the options being the ppa that was later mentioned by monkeybrain20122.

I normally only run servers, so I went to the "software center" on my desktop VM (but 14.10) and couldn't find ffmpeg.

---

### Post by FakeOutdoorsman on 2014-11-05
14.04 does not offer anything from FFmpeg. I believe it also no longer offers the counterfeit "ffmpeg" from Libav as has been forced to users in the past.

If you want a recent ffmpeg from FFmpeg see [Re: install ffmpeg on ubuntu 14.04](http://ubuntuforums.org/showthread.php?t=2249092&p=13147203&viewfull=1#post13147203) for several options. Even if the repo did offer ffmpeg it would often still be worth getting a more recent version due to how active the project is.

ffmpeg from FFmpeg is somewhere in the Debian process, I can't remember where exactly, so it will eventually return to Ubuntu, but given the sluggish pace of this process I'm not sure how long it will be.

---

### Post by mc4man on 2014-11-05
> **FakeOutdoorsman said:**
> 

ffmpeg from FFmpeg is somewhere in the Debian process, I can't remember where exactly, so it will eventually return to Ubuntu, but given the sluggish pace of this process I'm not sure how long it will be.
It could show up in 15.04 as already in Debian sid.  And it probably won't be as useful as any other means to use..

---

### Post by andrew.46 on 2014-11-05
> **mc4man said:**
> It could show up in 15.04 as already in Debian sid. 

Some hard work being done there:

[http://metadata.ftp-master.debian.org/changelogs//main/f/ffmpeg/ffmpeg_2.4.3-1_changelog](http://metadata.ftp-master.debian.org/changelogs//main/f/ffmpeg/ffmpeg_2.4.3-1_changelog)

---

### Post by mc4man on 2014-11-06
> **andrew.46 said:**
> Some hard work being done there:

[http://metadata.ftp-master.debian.org/changelogs//main/f/ffmpeg/ffmpeg_2.4.3-1_changelog](http://metadata.ftp-master.debian.org/changelogs//main/f/ffmpeg/ffmpeg_2.4.3-1_changelog)
I had put the new up the other day for trusty, decided to go ahead & integrate [here]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6") (atm only cmus uses the shared for a fix of  ffmpeg.so & only for users that want to fool around a bit...

Hadn't noticed new symbols avail.  so thanks for a reminder of sorts, currently adding.

---

