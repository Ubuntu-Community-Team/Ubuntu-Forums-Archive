---
title: "FFMPEG:  Failed to download repository information"
date: 2015-04-01
forum: General Help
---

### Post by feartheterrapin on 2015-04-01
Recntly, my Ubuntu 12.04 (64b) software updater is unable to update FFMPEG apparently because the repository no longer exists.  I received the following error:
 
 W:Failed to fetch [http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/precise/main/source/Sources)  404  Not Found 
 , W:Failed to fetch [http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found 
 , W:Failed to fetch [http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
 
 I assume the  jon-severinsson PPA is no longer supported.  I tried the following as a solution:
 
 sudo add-apt-repository ppa:mc3man/trusty-media
 sudo apt-get update
sudo apt-get dist-upgrade
 
 But ended up with different repositories that could not update.
 
 I use FFMPEG mostly to run Serviio.   I do not plan on upgrading to 14.04 as I will be update to 16.04 LTS when available.  What are my options to fix FFMPEG in 12.04?

---

### Post by ian-weisser on 2015-04-01
> **feartheterrapin said:**
> I assume the  jon-severinsson PPA is no longer supported.

Sort of.
Jon Severinsson is no longer supporting *their personal* PPA, and has closed it.


> **feartheterrapin said:**
> But ended up with different repositories that could not update.

Unfortunately, that happens with some PPAs. Sometimes the PPA software has issues...sometimes the user tries to add an inappropriate PPA.
Adding a Trusty (14.04) PPA to a Precise (12.04) system seems unlikely to work.


> **feartheterrapin said:**
> What are my options to fix FFMPEG in 12.04?

That would depend upon what's broken.
One answer is at [http://askubuntu.com/questions/426543/install-ffmpeg-in-ubuntu-12-04-lts](http://askubuntu.com/questions/426543/install-ffmpeg-in-ubuntu-12-04-lts)

---

### Post by feartheterrapin on 2015-04-02
So I did the following:

Removed jon-severinsson ppa
sudo ppa-purge ppa:jon-severinsson/ffmpeg

then followed the "one answer"
sudo apt-get install libav-tools
sudo apt-get install ffmpeg
(I was confused by the instructions: libav-tools or ffmpeg, but I did both)

No errors yet.

---

### Post by mc4man on 2015-04-02
> **ian-weisser said:**
> 

Unfortunately, that happens with some PPAs. Some people maintain packages well, others are...learning.


And some people, meaning you & the Op,  should learn how to read & comprehend better...

---

### Post by KushG on 2015-04-02
I'm sure your ppa is useful and appreciated by many.  I will add though that I, like the OP, was not able to use your repo as a replacement.  My particular issue was finding it is not compiled for https support.  I can't comment on anything else because I couldn't get past reading input. 

I'm confused by you saying the OP should learn how to read & comprehend better.

---

### Post by mc4man on 2015-04-02
> **KushG said:**
> I'm sure your ppa is useful and appreciated by many.  I will add though that I, like the OP, was not able to use your repo as a replacement.  My particular issue was finding it is not compiled for https support.  I can't comment on anything else because I couldn't get past reading input. 

I'm confused by you saying the OP should learn how to read & comprehend better.
If you had a reasonable reason to have https in the static ffmpeg then all you would have needed to do was request it via LP email. As far as the OP & the other guy is it not clear the ppa is for 14.04 (trusty) only??

---

### Post by feartheterrapin on 2015-04-02
> **mc4man said:**
> As far as the OP & the other guy is it not clear the ppa is for 14.04 (trusty) only??

I find these forums very helpful as most are very willing to help and provide suggestions.  My posting of my experience was never intended to be a slam on anyone, just trying to post all the information I can on my current challenge so I can get the best support.  I apologise if my original post offended you.

---

### Post by KushG on 2015-04-02
I see what you mean now.  The OP didn't have an actual issue with the ppa, he wants to run it on a version it's not supported on.  Gotcha!  Sorry I was confused and thought I might be missing something as well.

I'm sorry but I'm not quite sure what LP email is.  I use hls sources to capture media for making gifs, some are https only for whatever reason. 

Thanks :)

---

### Post by Bashing-om on 2015-04-02
Guys;

From what I am aware of:
ffmeg is no longer in the repo;
its "avconv" now ->  avconv is in libavtools.
 FFMpeg is coming back to Ubuntu in the next release -> [http://packages.ubuntu.com/vivid/ffmpeg](http://packages.ubuntu.com/vivid/ffmpeg)

my bit to try and help

---

### Post by FakeOutdoorsman on 2015-04-02
> **feartheterrapin said:**
> What are my options to fix FFMPEG in 12.04?
See the [compile guide](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu) or simply get a [static build](http://johnvansickle.com/ffmpeg/). However, I don't know what Serviio is or how it uses ffmpeg.

> **KushG said:**
> I'm sorry but I'm not quite sure what LP email is.
Launchpad ([here](https://launchpad.net/~mc3man/+contactuser) in particular regarding mc4man's PPA).

> **KushG said:**
> I use hls sources to capture media for making gifs, some are https only for whatever reason.
If you're making gifs with ffmpeg see: [High quality GIF with FFmpeg](http://blog.pkh.me/p/21-high-quality-gif-with-ffmpeg.html).

---

### Post by mc4man on 2015-04-02
While it would be simple to enable gnutls or openssl I'm not too sure it's that useful for a static build. Seems better suited to a shared ffmpeg build for players using libavformat, ect.
(I don't quite 'get' the above posted reason by KushG, illumination welcome.

---

### Post by KushG on 2015-04-02
Thanks Outdoorsman. I actually download video first, for use with other stuff in addition to the gifs.  Therefore the https support is imperative. :)  I figured no better time than now to learn to compile for myself and have it up and running flawlessly. I only use ubuntu for ffmpeg so it was a good lesson.

---

