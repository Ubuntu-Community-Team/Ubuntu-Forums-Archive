---
title: "Ubuntu 14.04,,ffmpeg,,and libavcodec.so.52"
date: 2014-04-27
forum: General Help
---

### Post by timsdeepsky on 2014-04-27
Hello again,,
I have searched many pages,,found no fixes,,and feel the need to clear my head and get back to the basics of my problem....
I have been using 12.04 and have not had this problem....
2 days ago i installed 14.04 on a new ssd,,and installed ffmpeg from here[https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide]("https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide")....
I installed this program [https://sites.google.com/site/linuxuhvo/]("https://sites.google.com/site/linuxuhvo/")....
This program worked on 12.04,,and the 3 releases prior to that....
It now gives me this error....
```
./UHVO: error while loading shared libraries: libavcodec.so.52: cannot open shared object file: No such file or directory

```
So i read a hundred pages like this one [http://ubuntuforums.org/showthread.php?t=1560374&highlight=libavcodec.so.52]("http://ubuntuforums.org/showthread.php?t=1560374&highlight=libavcodec.so.52"),,
I have tried to install "libavcodec.so.52" and it gives me this
```
tim@tim-GA-870A-UD3:~$ sudo apt-get install ffmpeg libavcodec-extra-52
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libavcodec-extra-52 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ffmpeg:i386 ffmpeg

E: Package 'libavcodec-extra-52' has no installation candidate

``` 
I have emailed the maintainers of the uhvo program also....
I am beginning to think it is a broken path maybe because of the libav/ffmpeg fork....

Ubuntu 14.04 LTS
64 bit system

ffmpeg version
```
tim@tim-GA-870A-UD3:~$ ffmpeg
ffmpeg version 2.2.git-66e30a2 Copyright (c) 2000-2014 the FFmpeg developers
  built on Apr 26 2014 22:17:03 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-x11grab --enable-libpulse --enable-libx264 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex --enable-libass --enable-avisynth
  libavutil      52. 79.100 / 52. 79.100
  libavcodec     55. 59.100 / 55. 59.100
  libavformat    55. 37.101 / 55. 37.101
  libavdevice    55. 13.100 / 55. 13.100
  libavfilter     4.  4.100 /  4.  4.100
  libavresample   1.  2.  0 /  1.  2.  0
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 18.100 /  0. 18.100
  libpostproc    52.  3.100 / 52.  3.100
```

Any info would be awesome....
Thank you....

---

### Post by timsdeepsky on 2014-05-11
Problem solved....
Finally fixed this issue on my own....
In 14.04 i had to compile ffmpeg from here [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu")....
Then go get "libavutil49" from here [http://packages.ubuntu.com/lucid/amd64/libavutil49/download]("http://packages.ubuntu.com/lucid/amd64/libavutil49/download"),,and install....
Then go get "libavcodec52" from here [http://packages.ubuntu.com/lucid/amd64/libs/libavcodec52]("http://packages.ubuntu.com/lucid/amd64/libs/libavcodec52"),,and install it....
I realise these are "lucid"....But i found no other way to do this....

---

### Post by monkeybrain20122 on 2014-05-12
This looks like a very old program and current ffmpeg most likely won't work, you can grab an old ffmpeg and then compile your program against it. Users of audacity are facing a similar problem and there is a tutorial to compile audacity against old ffmpeg, it may be useful for you too.[http://ubuntuforums.org/showthread.php?t=2219907](http://ubuntuforums.org/showthread.php?t=2219907)

---

### Post by timsdeepsky on 2014-05-12
Hi monkeybrain20122,,
I actually have this working now....A new compile of [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu") with the old lucid release of "libavutil49" and "libavcodec52"....
The maintainer of the program i was having issues with i could not get in touch with....So compiling their program was a no go....They have no source code available to download....It's just a downloadable executable that is already compiled....Sort of like a static program i guess....Anyway,,,,this is the only fix i have found for 14.04 (yay),,so now i will get to use 14.04 after all....
The whole ffmpeg/avconv thing is still confusing....14.04 comes with avconv,,,,and i am not sure if it has a library that is the same as these "libavutil49" and "libavcodec52" that a person could compile against if he could get the source....
Thanks for your time monkeybrain20122....

---

