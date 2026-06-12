---
title: "info-docs for all my installed programs"
date: 2013-10-19
forum: General Help
---

### Post by *PTR on 2013-10-19
I would like to install info-pages where there are such written for thoose programs which I have installed on my system.

Please escuse me for not being more clear in what I  want to do, if I could put it more simple and better . I am sure I could find it on google.

---

### Post by ibjsb4 on 2013-10-20
/usr/share/doc ?  Thats what comes to mind, but I don't think its a good place to store files.  Can you give us an example of info-pages

---

### Post by oldos2er on 2013-10-20
Any info pages will be installed when you install the program, as far as I know, and I'm not sure that every program has info pages available. Are there any particular programs you need help with?

---

### Post by *PTR on 2013-11-03
I have both avconv and *Real* ffmpeg installed. ffmpeg did I install from source.
For neither of them I have the info-files installed, but it seems as it exists for both.

ffmpeg:[https://github.com/FFmpeg/FFmpeg/blob/master/doc/ffmpeg.texi]("https://github.com/FFmpeg/FFmpeg/blob/master/doc/ffmpeg.texi")

avconv:[http://https://gitorious.org/ffmpeg/sastes-ffmpeg/source/f98edc73c599badaa0c075fbffb519a150d03d80:doc/avconv.texi]("http://https://gitorious.org/ffmpeg/sastes-ffmpeg/source/f98edc73c599badaa0c075fbffb519a150d03d80:doc/avconv.texi")

I also know that I have them in the folder from where I installed - eg git/fmpeg/doc. So I can go to that directory and run ```
info ./ffmpeg.texi
``` But I have no Idea how to install them from there, but thats not whats I am going to ask about.

I will find out myself how to install them from my  folder. I suppose that it is a flag to configure. 
Else I just could copy the files by hand.

What I really would like to know, if the info-files is not included whem I do an apt-get install, is there a parameter I can pass to get them while I install new software.?

Or could I tell apt to update all the missing info-files for one of my installed package,  for example, avconv.?

---

### Post by andrew.46 on 2013-11-04
Have you installed FFmpeg courtesy of the FFmpeg wiki? The docs (and there are some nice html docs in there) should be built in the presence of texi2html. On my non-ubuntu system I package the following:

```

andrew@skamandros/usr/share/doc/ffmpeg$**[COLOR="#FF0000"] ls -C[/COLOR]**
COPYING.GPLv2     errno.txt                      ffmpeg-scaler.html  git-howto.txt       optimization.txt
COPYING.GPLv3     faq.html                       ffmpeg-utils.html   issue_tracker.txt   platform.html
COPYING.LGPLv2.1  fate.html                      ffmpeg.SlackBuild   libavcodec.html     rate_distortion.txt
COPYING.LGPLv3    fate.txt                       ffmpeg.html         libavdevice.html    snow.txt
CREDITS           ffmpeg-all.html                ffmpeg.txt          libavfilter.html    soc.txt
Changelog         ffmpeg-bitstream-filters.html  ffplay-all.html     libavformat.html    swresample.txt
INSTALL           ffmpeg-codecs.html             ffplay.html         libavutil.html      swscale.txt
MAINTAINERS       ffmpeg-devices.html            ffprobe-all.html    libswresample.html  tablegen.txt
README            ffmpeg-filters.html            ffprobe.html        libswscale.html     viterbi.txt
avutil.txt        ffmpeg-formats.html            filter_design.txt   mips.txt
build_system.txt  ffmpeg-protocols.html          general.html        multithreading.txt
developer.html    ffmpeg-resampler.html          git-howto.html      nut.html
andrew@skamandros/usr/share/doc/ffmpeg$ 

```

although this could do with some weeding out :). Perhaps FakeOutdoorsman could suggest some additional syntax to package up the more useful docs into an easy to find location...

---

### Post by FakeOutdoorsman on 2013-11-04
> **andrew.46 said:**
> although this could do with some weeding out :). Perhaps FakeOutdoorsman could suggest some additional syntax to package up the more useful docs into an easy to find location...

The [ffmpeg compile guide](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) should install the html formatted docs to:
```
~/ffmpeg_build/share/doc/ffmpeg
```

I should mention that in the guide. I also haven't yet dealt with the man pages, unfortunately.

---

### Post by *PTR on 2013-11-04
Thanks for thoose great advices.
And now - back to topic :-)

How can I tell apt to install missing tex-info files for, for example avcomv - as it is not installed by default.?

---

### Post by Frogs Hair on 2013-11-04
I think you may have to bookmark that . [http://libav.org/avconv.html](http://libav.org/avconv.html)

---

### Post by FakeOutdoorsman on 2013-11-04
Online docs apply only to the code/builds from git master. Users of releases should refer to the documentation included in their package or build (if they are included).

---

### Post by *PTR on 2013-11-05
So if you use apt, there is no way to get the texi-files which originally is included in the buildtree.?

Does that mean that the ubuntu.developers selectively choose for us to not get the more informative texi documents  if we not search for them online.?

And yes, I know that there is lot of different document-formats on the web containing that info, but I would like to find a way so I as easily as possibly could read them within my beloved shell, and yo not have go and search for that info for every single program where I find the manpages is not enough.

---

### Post by *PTR on 2013-11-06
According to no replyes for my last question, which eg was the topic all the time, I gueess that's the case.  We are forced to seek the net if we want that information which is inclued in several programs buildtree, often in texi fromat.

Or should I put the question in some other place.?

---

