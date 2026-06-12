---
title: "Sound Converter not finding correct plugins"
date: 2014-04-27
forum: General Help
---

### Post by Joseph_OHara on 2014-04-27
Hello I am trying to install Pokemon Zeta from the PC version on my 14.04 system, and part of the process for the installation is converting files into .wav format. ([http://www.reddit.com/r/pokemonzetaomicron/comments/2146ub/how_to_run_pokemon_zetaomicron_on_ubuntu_1310/](http://www.reddit.com/r/pokemonzetaomicron/comments/2146ub/how_to_run_pokemon_zetaomicron_on_ubuntu_1310/)) (considering that while this is for 13.10 its the same problem) and I'm trying to use sound converter. However, when I attempt to convert the files, it says "python needs plugins" and searches for them, and comes up with gstreamer plugins like so:
 [IMG]http://i.imgur.com/8ciWPVU.png[/IMG]

But when I go for it, it says package dependencies could not be resolved and outputs the following in details:
[PHP] The following packages have unmet dependencies:
gstreamer0.10-plugins-bad: Depends: libc6 (>= 2.15) but 2.19-0ubuntu6 is to be installed                           Depends: libcairo2 (>= 1.2.4) but 1.13.0~20140204-0ubuntu1 is to be installed                           Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-13 is to be installed                           Depends: libcurl3-gnutls (>= 7.16.2) but 7.35.0-1ubuntu2 is to be installed                           Depends: libdvdnav4 (>= 4.1.3) but 4.2.1-3 is to be installed                           Depends: libdvdread4 (>= 4.1.3) but 4.2.1-2ubuntu1 is to be installed                           Depends: libfaad2 (>= 2.7) but 2.7-8 is to be installed                           Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed                           Depends: libglib2.0-0 (>= 2.37.3) but 2.40.0-2 is to be installed                           Depends: libgsm1 (>= 1.0.13) but 1.0.13-4 is to be installed                           Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.23-7.2ubuntu1) but 0.10.23-7.2ubuntu1 is to be installed                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1.1ubuntu2 is to be installed                           Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1.2ubuntu3 is to be installed                           Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu3 is to be installed                           Depends: libopenal1 (>= 1:1.13) but 1:1.14-4ubuntu1 is to be installed                           Depends: libopus0 (>= 1.0.3) but 1.1-0ubuntu1 is to be installed                           Depends: liborc-0.4-0 (>= 1:0.4.18) but 1:0.4.18-1ubuntu1 is to be installed                           Depends: libpng12-0 (>= 1.2.13-4) but 1.2.50-1ubuntu2 is to be installed                           Depends: librsvg2-2 (>= 2.14.4) but 2.40.2-1 is to be installed                           Depends: librtmp0 (>= 2.3) but 2.4+20121230.gitdf6c518-1 is to be installed                           Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-2ubuntu1 is to be installed                           Depends: libsndfile1 (>= 1.0.20) but 1.0.25-7ubuntu2 is to be installed                           Depends: libsoundtouch0 (>= 1.7.1-3~) but 1.7.1-5 is to be installed                           Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1f-1ubuntu2 is to be installed                           Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed                           Depends: libvpx1 (>= 1.0.0) but 1.3.0-2 is to be installed                           Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-9ubuntu1 is to be installedgstreamer0.10-plugins-bad:i386: Depends: libc6 (>= 2.15) but 2.19-0ubuntu6 is to be installed                                Depends: libcairo2 (>= 1.2.4) but 1.13.0~20140204-0ubuntu1 is to be installed                                Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-13 is to be installed                                Depends: libcurl3-gnutls (>= 7.16.2) but 7.35.0-1ubuntu2 is to be installed                                Depends: libdvdnav4 (>= 4.1.3) but 4.2.1-3 is to be installed                                Depends: libdvdread4 (>= 4.1.3) but 4.2.1-2ubuntu1 is to be installed                                Depends: libfaad2 (>= 2.7) but 2.7-8 is to be installed                                Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed                                Depends: libglib2.0-0 (>= 2.37.3) but 2.40.0-2 is to be installed                                Depends: libgsm1 (>= 1.0.13) but 1.0.13-4 is to be installed                                Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.23-7.2ubuntu1) but 0.10.23-7.2ubuntu1 is to be installed                                Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1.1ubuntu2 is to be installed                                Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1.2ubuntu3 is to be installed                                Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu3 is to be installed                                Depends: libopenal1 (>= 1:1.13) but 1:1.14-4ubuntu1 is to be installed                                Depends: libopus0 (>= 1.0.3) but 1.1-0ubuntu1 is to be installed                                Depends: liborc-0.4-0 (>= 1:0.4.18) but 1:0.4.18-1ubuntu1 is to be installed                                Depends: libpng12-0 (>= 1.2.13-4) but 1.2.50-1ubuntu2 is to be installed                                Depends: librsvg2-2 (>= 2.14.4) but 2.40.2-1 is to be installed                                Depends: librtmp0 (>= 2.3) but 2.4+20121230.gitdf6c518-1 is to be installed                                Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-2ubuntu1 is to be installed                                Depends: libsndfile1 (>= 1.0.20) but 1.0.25-7ubuntu2 is to be installed                                Depends: libsoundtouch0 (>= 1.7.1-3~) but 1.7.1-5 is to be installed                                Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1f-1ubuntu2 is to be installed                                Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed                                Depends: libvpx1 (>= 1.0.0) but 1.3.0-2 is to be installed                                Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-9ubuntu1 is to be installedlibchromaprint0: Depends: libavcodec-extra-54 (>= 6:9.10) but 6:9.11-2ubuntu2 is to be installed                 Depends: libavutil52 (>= 6:9.1-1) but 6:9.11-2ubuntu2 is to be installed                 Depends: libc6 (>= 2.14) but 2.19-0ubuntu6 is to be installed                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed                 Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed
[/PHP]

I do not know what I can do, but if anyone can help it would be awesome. The game crashes because it cannot read certain audio files, so if I dont convert the files I cannot play the game. I am pretty new with ubuntu so if you guys could please go easy with the lingo. Thank you!

If anyone else got Pokemon Zeta to work using a different method please let me know and guide me through it!

---

### Post by Joseph_OHara on 2014-04-27
(Ignore the php code use this
>  The following packages have unmet dependencies:

gstreamer0.10-plugins-bad: Depends: libc6 (>= 2.15) but 2.19-0ubuntu6 is to be installed
                           Depends: libcairo2 (>= 1.2.4) but 1.13.0~20140204-0ubuntu1 is to be installed
                           Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-13 is to be installed
                           Depends: libcurl3-gnutls (>= 7.16.2) but 7.35.0-1ubuntu2 is to be installed
                           Depends: libdvdnav4 (>= 4.1.3) but 4.2.1-3 is to be installed
                           Depends: libdvdread4 (>= 4.1.3) but 4.2.1-2ubuntu1 is to be installed
                           Depends: libfaad2 (>= 2.7) but 2.7-8 is to be installed
                           Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
                           Depends: libglib2.0-0 (>= 2.37.3) but 2.40.0-2 is to be installed
                           Depends: libgsm1 (>= 1.0.13) but 1.0.13-4 is to be installed
                           Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.23-7.2ubuntu1) but 0.10.23-7.2ubuntu1 is to be installed
                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1.1ubuntu2 is to be installed
                           Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1.2ubuntu3 is to be installed
                           Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu3 is to be installed
                           Depends: libopenal1 (>= 1:1.13) but 1:1.14-4ubuntu1 is to be installed
                           Depends: libopus0 (>= 1.0.3) but 1.1-0ubuntu1 is to be installed
                           Depends: liborc-0.4-0 (>= 1:0.4.18) but 1:0.4.18-1ubuntu1 is to be installed
                           Depends: libpng12-0 (>= 1.2.13-4) but 1.2.50-1ubuntu2 is to be installed
                           Depends: librsvg2-2 (>= 2.14.4) but 2.40.2-1 is to be installed
                           Depends: librtmp0 (>= 2.3) but 2.4+20121230.gitdf6c518-1 is to be installed
                           Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-2ubuntu1 is to be installed
                           Depends: libsndfile1 (>= 1.0.20) but 1.0.25-7ubuntu2 is to be installed
                           Depends: libsoundtouch0 (>= 1.7.1-3~) but 1.7.1-5 is to be installed
                           Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1f-1ubuntu2 is to be installed
                           Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed
                           Depends: libvpx1 (>= 1.0.0) but 1.3.0-2 is to be installed
                           Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-9ubuntu1 is to be installed
gstreamer0.10-plugins-bad:i386: Depends: libc6 (>= 2.15) but 2.19-0ubuntu6 is to be installed
                                Depends: libcairo2 (>= 1.2.4) but 1.13.0~20140204-0ubuntu1 is to be installed
                                Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-13 is to be installed
                                Depends: libcurl3-gnutls (>= 7.16.2) but 7.35.0-1ubuntu2 is to be installed
                                Depends: libdvdnav4 (>= 4.1.3) but 4.2.1-3 is to be installed
                                Depends: libdvdread4 (>= 4.1.3) but 4.2.1-2ubuntu1 is to be installed
                                Depends: libfaad2 (>= 2.7) but 2.7-8 is to be installed
                                Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
                                Depends: libglib2.0-0 (>= 2.37.3) but 2.40.0-2 is to be installed
                                Depends: libgsm1 (>= 1.0.13) but 1.0.13-4 is to be installed
                                Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.23-7.2ubuntu1) but 0.10.23-7.2ubuntu1 is to be installed
                                Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1.1ubuntu2 is to be installed
                                Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1.2ubuntu3 is to be installed
                                Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu3 is to be installed
                                Depends: libopenal1 (>= 1:1.13) but 1:1.14-4ubuntu1 is to be installed
                                Depends: libopus0 (>= 1.0.3) but 1.1-0ubuntu1 is to be installed
                                Depends: liborc-0.4-0 (>= 1:0.4.18) but 1:0.4.18-1ubuntu1 is to be installed
                                Depends: libpng12-0 (>= 1.2.13-4) but 1.2.50-1ubuntu2 is to be installed
                                Depends: librsvg2-2 (>= 2.14.4) but 2.40.2-1 is to be installed
                                Depends: librtmp0 (>= 2.3) but 2.4+20121230.gitdf6c518-1 is to be installed
                                Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-2ubuntu1 is to be installed
                                Depends: libsndfile1 (>= 1.0.20) but 1.0.25-7ubuntu2 is to be installed
                                Depends: libsoundtouch0 (>= 1.7.1-3~) but 1.7.1-5 is to be installed
                                Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1f-1ubuntu2 is to be installed
                                Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed
                                Depends: libvpx1 (>= 1.0.0) but 1.3.0-2 is to be installed
                                Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-9ubuntu1 is to be installed
libchromaprint0: Depends: libavcodec-extra-54 (>= 6:9.10) but 6:9.11-2ubuntu2 is to be installed
                 Depends: libavutil52 (>= 6:9.1-1) but 6:9.11-2ubuntu2 is to be installed
                 Depends: libc6 (>= 2.14) but 2.19-0ubuntu6 is to be installed
                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
                 Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed




---

### Post by Cariboo1938 on 2014-04-30
Hello,
I am running xubuntu 14.04 for six days now. Also "xubuntu restricted extras" is installed, I have a similar issue.
 When I start Sound Converter for .flac to.mp3 conversion I get:
    "GStreamer Error. GStreamer encounterred a general stream error."
 I wonder if that is related to Joseph_OHara's problem? What else is missing? 
Any help is highly appreciated!

---

### Post by Yellow Pasque on 2014-04-30
[http://yoten.blogspot.com/2007/07/convert-midi-to-wav.html](http://yoten.blogspot.com/2007/07/convert-midi-to-wav.html)

---

### Post by tarsem_singh on 2014-09-29
Hi, I found the following command on some forum and now my mp3's and sounds are working again.
Try this: sudo apt-get install gstreamer1.0-fluendo-mp3 gstreamer0.10-fluendo-mp3Thanks

---

### Post by Nguyen_Xuan_Loc on 2014-12-14
> **tarsem_singh said:**
> Hi, I found the following command on some forum and now my mp3's and sounds are working again.
Try this: sudo apt-get install gstreamer1.0-fluendo-mp3 gstreamer0.10-fluendo-mp3Thanks

Thanks so much tarsem_singh. This worked for me.

---

### Post by kjsphoto on 2014-12-27
I followed all the notes in this thread and added more dependencies.  It says everything exists but I still get errors. I cannot get sound converter to work.  Here is the error message I am getting.  Ubuntu 14.

sudo apt-get install gstreamer1.0-fluendo-mp3 gstreamer0.10-fluendo-mp3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-fluendo-mp3 is already the newest version.
gstreamer1.0-fluendo-mp3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 309 not upgraded.


I am at a loss.  Anyone?


 The following packages have unmet dependencies:

gstreamer0.10-plugins-bad:i386: Depends: libc6 (>= 2.15) but 2.19-0ubuntu6.4 is to be installed
                                Depends: libcairo2 (>= 1.2.4) but 1.13.0~20140204-0ubuntu1 is to be installed
                                Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-13 is to be installed
                                Depends: libcurl3-gnutls (>= 7.16.2) but 7.35.0-1ubuntu2.2 is to be installed
                                Depends: libdvdnav4 (>= 4.1.3) but 4.2.1-3 is to be installed
                                Depends: libdvdread4 (>= 4.1.3) but 4.2.1-2ubuntu1 is to be installed
                                Depends: libfaad2 (>= 2.7) but 2.7-8 is to be installed
                                Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed
                                Depends: libglib2.0-0 (>= 2.37.3) but 2.40.2-0ubuntu1 is to be installed
                                Depends: libgsm1 (>= 1.0.13) but 1.0.13-4 is to be installed
                                Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.23-7.2ubuntu1) but 0.10.23-7.2ubuntu1 is to be installed
                                Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1.1ubuntu2 is to be installed
                                Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1.2ubuntu3 is to be installed
                                Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu3 is to be installed
                                Depends: libopenal1 (>= 1:1.13) but 1:1.14-4ubuntu1 is to be installed
                                Depends: libopus0 (>= 1.0.3) but 1.1-0ubuntu1 is to be installed
                                Depends: liborc-0.4-0 (>= 1:0.4.18) but 1:0.4.18-1ubuntu1 is to be installed
                                Depends: libpng12-0 (>= 1.2.13-4) but 1.2.50-1ubuntu2 is to be installed
                                Depends: librsvg2-2 (>= 2.14.4) but 2.40.2-1 is to be installed
                                Depends: librtmp0 (>= 2.3) but 2.4+20121230.gitdf6c518-1 is to be installed
                                Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-2ubuntu1 is to be installed
                                Depends: libsndfile1 (>= 1.0.20) but 1.0.25-7ubuntu2 is to be installed
                                Depends: libsoundtouch0 (>= 1.7.1-3~) but 1.7.1-5 is to be installed
                                Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1f-1ubuntu2.7 is to be installed
                                Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed
                                Depends: libvpx1 (>= 1.0.0) but 1.3.0-2 is to be installed
                                Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-9ubuntu1 is to be installed
libchromaprint0: Depends: libavcodec-extra-54 (>= 6:9.10) but 7:1.2.6-1~trusty1 is to be installed
                 Depends: libavutil52 (>= 6:9.1-1) but 7:1.2.6-1~trusty1 is to be installed
                 Depends: libc6 (>= 2.14) but 2.19-0ubuntu6.4 is to be installed
                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed
                 Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed

---

