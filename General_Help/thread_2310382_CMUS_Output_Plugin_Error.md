---
title: "CMUS Output Plugin Error"
date: 2016-01-18
forum: General Help
---

### Post by jonathan90 on 2016-01-18
Hello everyone! I had cmus 2.5tried installing cmus 2.7.1 (as a tarball) from cmus's website since the software center only had 2.5. After I installed it, I got this error message: "Error: selecting output plugin '': no such plugin." I was worried that I messed something up so I uninstalled it with "sudo make uninstall" and got 2.5 back from the software center. However, I still get the same error when I launch 2.5 now. Any help is greatly appreciated! Thanks!

This is the output when I run cmus --plugins.

Input Plugins: /usr/lib/cmus/ip
  mad:
    Priority: 55
    File Types: mp3 mp2
    MIME Types: audio/mpeg audio/x-mp3 audio/x-mpeg
  aac:
    Priority: 50
    File Types: aac
    MIME Types: audio/aac audio/aacp
  mpc:
    Priority: 50
    File Types: mpc mpp mp+
    MIME Types: audio/x-musepack
  wav:
    Priority: 50
    File Types: wav
    MIME Types:
  modplug:
    Priority: 50
    File Types: mod s3m xm it 669 amf ams dbm dmf dsm far mdl med mtm okt ptm stm ult umx mt2 psm
    MIME Types:
  cdio:
    Priority: 50
    File Types:
    MIME Types: x-content/audio-cdda
  flac:
    Priority: 50
    File Types: flac fla
    MIME Types:
  wavpack:
    Priority: 50
    File Types: wv
    MIME Types: audio/x-wavpack
  vorbis:
    Priority: 50
    File Types: ogg
    MIME Types: application/ogg audio/x-ogg
  ffmpeg:
    Priority: 30
    File Types: ac3 aif aifc aiff ape au mka shn tta wma aac fla flac m4a m4b mp+ mp2 mp3 mp4 mpc mpp ogg wav wv
    MIME Types:

Output Plugins: /usr/lib/cmus/op
  pulse
  alsa
  ao

---

### Post by QDR06VV9 on 2016-01-18
EDIT: There is a PPA for cmus also
[https://launchpad.net/~mc3man/+archive/ubuntu/aqua-tests](https://launchpad.net/~mc3man/+archive/ubuntu/aqua-tests)

If you are installing cmus from source,you also need to install all the dependencies.

Have a Look through this!
Deps:
> libcue 
ncurses 
alsa-lib (optional) - for ALSA output plugin support 
faad2 (optional) - for AAC input plugin support 
ffmpeg (optional) - for ffmpeg input plugin support 
flac (optional) - for flac input plugin support 
libao (optional) - for AO output plugin support 
libcdio-paranoia (optional) - for cdio support 
libmad (optional) - for mp3 input plugin support 
libmodplug (optional) - for modplug input plugin support 
libmp4v2 (optional) - for mp4 input plugin support 
libmpcdec (optional) - for musepack input plugin support 
libpulse (optional) - for PulseAudio output plugin support 
libvorbis (optional) - for vorbis input plugin support 
opusfile (optional) - for opus input plugin support 
wavpack (optional) - for wavpack input plugin support 
faad2 (make) 
ffmpeg (make) 
flac (make) 
libao (make) 
libcdio-paranoia (make) 
libmad (make) 
libmodplug (make) 
libmp4v2 (make) 
libmpcdec (make) 
libpulse (make) 
libvorbis (make) 
opusfile (make) 
wavpack (make)

From Here [https://github.com/cmus/cmus/issues/197](https://github.com/cmus/cmus/issues/197)
[COLOR=#333333][FONT=Helvetica Neue]Found the list of library on an ArchLinux page ([https://www.archlinux.org/packages/community/x86_64/cmus/](https://www.archlinux.org/packages/community/x86_64/cmus/))[/FONT][/COLOR]

---

### Post by jonathan90 on 2016-01-18
Sorry, I'm kinda new to installing through tarballs. How would I install those dependencies?

---

### Post by mc4man on 2016-01-18
> **jonathan90 said:**
> Sorry, I'm kinda new to installing through tarballs. How would I install those dependencies?
Just curious, which release of ubuntu (14.04/trusty, 15.10/wily, ect.

---

### Post by QDR06VV9 on 2016-01-18
@mc4man
I was able to get Version 2.7.0-1 installed with your PPA on Trusty
```
me@TheGhost:~$ lsb_release -a && apt-cache policy cmusNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty
cmus:
  Installed: 2.7.0-1build1
  Candidate: 2.7.0-1build1
  Version table:
 *** 2.7.0-1build1 0
        500 http://ppa.launchpad.net/mc3man/aqua-tests/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status
     2.5.0-4build1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages



```

---

### Post by mc4man on 2016-01-18
> **runrickus said:**
> @mc4man
I was able to get Version 2.7.0-1 installed with your PPA on Trusty
```
me@TheGhost:~$ lsb_release -a && apt-cache policy cmusNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty
cmus:
  Installed: 2.7.0-1build1
  Candidate: 2.7.0-1build1
  Version table:
 *** 2.7.0-1build1 0
        500 http://ppa.launchpad.net/mc3man/aqua-tests/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status
     2.5.0-4build1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages



```
That one for trusty disables libav in cmus as it was broken & not fixable. 
(though I did add .m4a & .mp4 support
The wily build there does include ffmpeg support & in the upcoming 16.04/xenial the Ubuntu repo cmus is now up to date with ffmpeg support

---

### Post by QDR06VV9 on 2016-01-18
> **mc4man said:**
> That one for trusty disables libav in cmus as it was broken & not fixable. 
(though I did add .m4a & .mp4 support
The wily build there does include ffmpeg support & in the upcoming 16.04/xenial the Ubuntu repo cmus is now up to date with ffmpeg support
The wily is the one I installed and all is good..albeit the ffmpeg-plugin had unmet deps..
Think i will try to install the xenial version now.
**EDIT:** Just did and nothing new..

---

### Post by mc4man on 2016-01-18
> **runrickus said:**
> @mc4man
I was able to get Version 2.7.0-1 installed with your PPA on Trusty

I see - you installed the wily cmus package in trusty 
(the ffmpeg plugin package for wily would not be installable in trusty, there is a trusty 2.7.0 cmus with a ffmpeg plugin package elsewhere but not for for new users..

The control file/build-deps for 14.04 sans ffmpeg plugin would be - 
```
Build-Depends:
 debhelper (>= 9.0.0),
 libao-dev,
 libasound2-dev (>= 1.0.11) [linux-any],
 libcddb2-dev,
 libcdio-cdda-dev,
 libcue-dev,
 libfaad-dev,
 libflac-dev,
 libjack-jackd2-dev,
 libmad0-dev,
 libmp4v2-dev,
 libmodplug-dev,
 libmpcdec-dev,
 libncursesw5-dev,
 libopusfile-dev,
 libpulse-dev (>= 0.9.19),
 libroar-dev,
 libsamplerate0-dev,
 libvorbis-dev,
 libwavpack-dev,
 pkg-config
```

---

### Post by QDR06VV9 on 2016-01-18
> **mc4man said:**
> I see - you installed the wily cmus package in trusty 
(the ffmpeg plugin package for wily would not be installable in trusty, there is a trusty 2.7.0 cmus with a ffmpeg plugin package elsewhere but not for for new users..

The control file/build-deps for 14.04 sans ffmpeg plugin would be - 
```
Build-Depends:
 debhelper (>= 9.0.0),
 libao-dev,
 libasound2-dev (>= 1.0.11) [linux-any],
 libcddb2-dev,
 libcdio-cdda-dev,
 libcue-dev,
 libfaad-dev,
 libflac-dev,
 libjack-jackd2-dev,
 libmad0-dev,
 libmp4v2-dev,
 libmodplug-dev,
 libmpcdec-dev,
 libncursesw5-dev,
 libopusfile-dev,
 libpulse-dev (>= 0.9.19),
 libroar-dev,
 libsamplerate0-dev,
 libvorbis-dev,
 libwavpack-dev,
 pkg-config
```
Thank You Sir!:D

---

### Post by mc4man on 2016-01-18
> **jonathan90 said:**
> Hello everyone! I had cmus 2.5tried installing cmus 2.7.1 (as a tarball) from cmus's website since the software center only had 2.5. After I installed it, I got this error message: "Error: selecting output plugin '': no such plugin."
does this work?
```
cmus :set output_plugin=pulse
```

---

### Post by jonathan90 on 2016-01-18
I'm using 2.5 right now and somehow it's working again. I tried ":set output_plugin=pulse" and I'm not sure if it did it but something did. :D By the way, I have Ubuntu 14.04.

---

