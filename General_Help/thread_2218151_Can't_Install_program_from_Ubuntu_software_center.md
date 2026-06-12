---
title: "Can't Install program from Ubuntu software center"
date: 2014-04-19
forum: General Help
---

### Post by ntdyok on 2014-04-19
I'm currently running Ubuntu 14.04 LTS. I want to install a program from the software centre but this message keeps popping up:

Package dependencies cannot be resolved

Details:

The following packages have unmet dependencies:
youtube-to-mp3: Depends: libc6 (>= 2.14) but 2.19-0ubuntu6 is to be installed
                Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
                Depends: libqt4-declarative (>= 4:4.7.0~rc1) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
                Depends: libqt4-network (>= 4:4.6.1) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
                Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
                Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
                Depends: libstdc++6 (>= 4.6) but 4.8.2-19ubuntu1 is to be installed
                Depends: libav-tools (>= 4:0.8.6-0ubuntu0.12.04.1) but 6:9.11-2ubuntu2 is to be installed
                Depends: libavcodec-extra-53 (>= 4:0.8.6ubuntu0.12.04.1) but it is not going to be installed
                Depends: libmp3lame0 (>= 3.99.3+repack1-1) but 3.99.5+repack1-3ubuntu1 is to be installed

I'm also very new to Ubuntu, so any additional help will be appreciated. Thanks in advance.

---

### Post by SeijiSensei on 2014-04-20
Try running "sudo apt-get update" from a command prompt and see if that helps.

---

### Post by ntdyok on 2014-04-20
> **SeijiSensei said:**
> Try running "sudo apt-get update" from a command prompt and see if that helps.

I ran it... I'm still getting the error message.

---

### Post by 23dornot23d on 2014-04-20
Which ppa is that coming from ...... ?

youtube-to-mp3

as I cannot see it in the normal repos

All I can find is this when searching for it - but its for a older version of Ubuntu ......
[http://askubuntu.com/questions/218932/convert-youtube-to-mp3](http://askubuntu.com/questions/218932/convert-youtube-to-mp3)

---

### Post by ibjsb4 on 2014-04-20
> Depends: libavcodec-extra-53 (>= 4:0.8.6ubuntu0.12.04.1) but it is not going to be installed

That package is not available in 14.04

[http://packages.ubuntu.com/precise/libavcodec-extra-53](http://packages.ubuntu.com/precise/libavcodec-extra-53)

---

### Post by ntdyok on 2014-04-20
> **ibjsb4 said:**
> That package is not available in 14.04

[http://packages.ubuntu.com/precise/libavcodec-extra-53](http://packages.ubuntu.com/precise/libavcodec-extra-53)

So... it won't download because it's not up to date?

---

### Post by ibjsb4 on 2014-04-20
Like 23d, I think you need to remove 'youtube-to-mp3'

---

### Post by bportoulas on 2015-03-10
I had the same problem and dont know what caused it cause im not an ubuntu expert.the point though is that i went to the page [http://www.mediahuman.com/download.html](http://www.mediahuman.com/download.html)
which is the official page and download it ubuntu 64-bit and it worked.hope i helped

---

### Post by oldos2er on 2015-03-10
Old thread closed.

---

