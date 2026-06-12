---
title: "ffmpeg"
date: 2013-08-29
forum: General Help
---

### Post by royalist10 on 2013-08-29
Why is ffmpeg deprecated ??:o :( and where is the avconv package located please?

Using Ubuntu 12.10

---

### Post by 1/0 on 2013-08-29
[http://ubuntuforums.org/showthread.php?t=1995559]("http://ubuntuforums.org/showthread.php?t=1995559")

---

### Post by speartip on 2013-08-29
The ffmpeg package is still being developed as far as I know.
To install the latest version you need to add this ppa to your sources:
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

---

### Post by FakeOutdoorsman on 2013-08-29
> **royalist10 said:**
> Why is ffmpeg deprecated ??:o :( and where is the avconv package located please?

Using Ubuntu 12.10

The "deprecated" message was designed to mislead users on purpose. The fake, so-called ffmpeg from the fork has been deprecated for avconv. Development of real ffmpeg from FFmpeg is very active. See:

[list]
[*][Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017)
[*][The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)
[/list]


> **speartip said:**
> To install the latest version you need to add this ppa to your sources:
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

Unfortunately this PPA only supplies the 0.10 and 0.7 release branches which are considered to be old for general users.

Your best options for using an up-to-date ffmpeg from FFmpeg are:

[list]
[*]Simply use a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) (see [instructions](http://askubuntu.com/a/270107/59378)), or
[*]Follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)
[/list]

---

