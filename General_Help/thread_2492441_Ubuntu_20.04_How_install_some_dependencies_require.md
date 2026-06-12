---
title: "Ubuntu 20.04 How install some dependencies required for ffmpeg 4.4.3 ?"
date: 2023-11-11
forum: General Help
---

### Post by aug7744 on 2023-11-11
Hello.
Thanks for reading my topic.
I have tested install ffmpeg 4.4.3 in focal 20.04, but has requirement of dependencies below :

librav1e0
libsvtav1enc1
librist4
libvmaf1

Ubuntu packages and others areas not have any information about install it.
I remember being possible installing 4.4.3 in focal 20.04 using PPA from [https://launchpad.net/~savoury1/+archive/ubuntu/ffmpeg4](https://launchpad.net/~savoury1/+archive/ubuntu/ffmpeg4).
However the PPA owner have disabled GPU enconding acceleration in current ffmpeg builds and removed previous version too.
I not have information if PPA owner [https://launchpad.net/~savoury1/+archive/ubuntu/ffmpeg4](https://launchpad.net/~savoury1/+archive/ubuntu/ffmpeg4) had the dependencies and was removed too.

I only want ffmpeg with Nvidia nvenc acceleration for geforce 600 kepler. Have some ffmpeg current builds not having acceleration for geforce 600.

Have an nice day.

---

### Post by MAFoElffen on 2023-11-12
???
RE: [https://packages.ubuntu.com/focal/ffmpeg](https://packages.ubuntu.com/focal/ffmpeg)

Those are the dependencies for that package in the Focal Repo's.  The dependencies you listed are not listed there.

I am a bit curious why ffmpeg?I mean I have done NVidia for almost 20 years now. But the last time I used ffmpeg was over 10 years ago. (Ubuntu 12.04) What do you need that you are not getting?

---

### Post by aug7744 on 2023-11-12
Thanks for reply.
In [https://packages.ubuntu.com/focal/ffmpeg](https://packages.ubuntu.com/focal/ffmpeg) list dependencies for ffmpeg 4.2.7. Not for 4.4.3.

Have some good softwares ( Shutter Enconder , OBS Studio and others) requiring FFMPEG version compatible with others libraries dependencies so the minimum is 4.4.3.
I see some FFMPEG compiled builds, but not work for driver 470 with NVENC for GeForce 600 Kepler.
I my tests 4.4.3 is the last version having NVENC acceleration for Kepler.

---

### Post by MAFoElffen on 2023-11-12
Yes, and: Jammy=4.4-2, Lunar=5.1-2 & Lunar=6.0-6, Noble so far is 6.0-9

You could always compile and install from source: [https://support.assetbank.co.uk/hc/en-gb/articles/115006491547-Installing-Ffmpeg-on-Linux](https://support.assetbank.co.uk/hc/en-gb/articles/115006491547-Installing-Ffmpeg-on-Linux)
RE: [https://ffmpeg.org/](https://ffmpeg.org/)    <-- Current latest is 6.1

That ~savoury PPA has been broken for over a year. I think the maintainer crippled it, when he figured that he wanted to make money from doing that.

---

