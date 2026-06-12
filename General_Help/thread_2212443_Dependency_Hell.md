---
title: "Dependency Hell"
date: 2014-03-21
forum: General Help
---

### Post by cmcanulty on 2014-03-21
I am trying to install YouTube to MP3 in 12.04 and get numerous dependencies required. I can't install any of the dependencies from synaptic without more dependency problems it is in the software center and I had it installed once before without any issues
```
The following packages have unmet dependencies:

youtube-to-mp3: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.5 is to be installed
                Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                Depends: libqt4-declarative (>= 4:4.7.0~rc1) but 4:4.8.1-0ubuntu4.6 is to be installed
                Depends: libqt4-network (>= 4:4.6.1) but 4:4.8.1-0ubuntu4.6 is to be installed
                Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.6 is to be installed
                Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.6 is to be installed
                Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
                Depends: libav-tools (>= 4:0.8.6-0ubuntu0.12.04.1) but 4:0.8.1-0ubuntu1 is to be installed
                Depends: libavcodec-extra-53 (>= 4:0.8.6ubuntu0.12.04.1) but 4:0.8.9ubuntu0.12.04.1 is to be installed
                Depends: libmp3lame0 (>= 3.99.3+repack1-1) but 3.99.3+repack1-1 is to be installed
```

I also tried using directions from here
[http://linuxaria.com/pills/how-to-convert-youtube-video-to-mp3-easily-on-gnulinux?lang=en]("http://linuxaria.com/pills/how-to-convert-youtube-video-to-mp3-easily-on-gnulinux?lang=en")

---

### Post by buzzingrobot on 2014-03-21
Have you kept your system current with the updates?

Have you tried "sudo apt-get -f install" as suggested at Linuxaria?

---

### Post by coldraven on 2014-03-21
Try youtube-dl instead
[http://www.webupd8.org/2014/02/video-downloader-youtube-dl-gets.html](http://www.webupd8.org/2014/02/video-downloader-youtube-dl-gets.html)

---

### Post by andrew.46 on 2014-03-22
> **coldraven said:**
> Try youtube-dl instead
[http://www.webupd8.org/2014/02/video-downloader-youtube-dl-gets.html](http://www.webupd8.org/2014/02/video-downloader-youtube-dl-gets.html)

The article leaves out one great feature: youtube-dl can source a configuration file most conveniently located as  *~/.config/youtube-dl.conf* so complex commandlines can be made a little easier :)

---

### Post by cmcanulty on 2014-03-22
yes I update every day. I decided to do it with online video2mp3 and leave my system alone, thanks. It seems odd to have an app in the software center with unsatisfiable dependencies

---

### Post by buzzingrobot on 2014-03-22
The version in Software Center is listed as 2.6.8.  The Ubuntu version listed at the MediaHuman site ([http://www.mediahuman.com/download.html](http://www.mediahuman.com/download.html)) is 3.3.

---

