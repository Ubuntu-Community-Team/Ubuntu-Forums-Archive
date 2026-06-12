---
title: "I have unresolved package dependency problems with MPEG etc"
date: 2014-01-15
forum: General Help
---

### Post by deaton25 on 2014-01-15
I installed an internet radio portal recently. Many of the stations on the platform don't play because I am supposed to install MPEG stuff. Except I Already installed all this stuff when I downloaded Ubuntu Restricted.Then they keep asking me to install the same stuff over and over again. It's like it doesn't register! Then I get messages about Unresolved 
Package Dependencies--whatever that means. Can you help me make some sense of this stuff and tell me how to fix it>Thanks

```
The following packages have unmet dependencies:


gstreamer0.10-ffmpeg:i386: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.9ubuntu0.12.04.1 is to be installed
                           Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.9ubuntu0.12.04.1 is to be installed
                           Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.9ubuntu0.12.04.1 is to be installed
                           Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.5 is to be installed
                           Depends: libglib2.0-0 (>= 2.31.2) but 2.32.4-0ubuntu1 is to be installed
                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu0.1 is to be installed
                           Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                           Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                           Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.9ubuntu0.12.04.1 is to be installed
                           Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.9ubuntu0.12.04.1 is to be installed
gstreamer0.10-plugins-bad:i386: Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.5 is to be installed
                                Depends: libcairo2 (>= 1.2.4) but 1.10.2-6.1ubuntu3 is to be installed
                                Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-10build1 is to be installed
                                Depends: libcurl3-gnutls (>= 7.16.2-1) but 7.22.0-3ubuntu4.6 is to be installed
                                Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                Depends: libglib2.0-0 (>= 2.31.8) but 2.32.4-0ubuntu1 is to be installed
                                Depends: libgsm1 (>= 1.0.13) but 1.0.13-3 is to be installed
                                Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.22.3-2ubuntu2.2) but 0.10.22.3-2ubuntu2.2 is to be installed
                                Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1ubuntu0.1 is to be installed
                                Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1ubuntu1 is to be installed
                                Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu1 is to be installed
                                Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is to be installed
                                Depends: libopenspc0 but it is not going to be installed
                                Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                Depends: libpng12-0 (>= 1.2.13-4) but 1.2.46-3ubuntu4 is to be installed
                                Depends: librsvg2-2 (>= 2.14.4) but 2.36.1-0ubuntu1 is to be installed
                                Depends: librtmp0 (>= 2.3) but 2.4~20110711.gitc28f1bab-1 is to be installed
                                Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-1 is to be installed
                                Depends: libsndfile1 (>= 1.0.20) but 1.0.25-4 is to be installed
                                Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1-4ubuntu5.11 is to be installed
                                Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
                                Depends: libvpx1 (>= 1.0.0) but 1.0.0-1 is to be installed
                                Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-6 is to be installed
```

---

### Post by Bucky Ball on 2014-01-16
Do these two commands, hitting return between each:

```
sudo apt-get update
sudo apt-get upgrade
```

Report any issues. Looks like you haven't done any updates or haven't done any in awhile. 12.04 is currently at 12.04.3 and looks like you are trying to get packages for 12.04.1. Once your up to date then that should resolve your issue.

PS: I have put your code between [code] tags. Please use them in future. Thanks. ;)

---

