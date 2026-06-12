---
title: "Getting Kaffeine to play DVDs - Xubuntu"
date: 2007-05-23
forum: General Help
---

### Post by geovino on 2007-05-23
I can't get Kaffeine to play a DVD. I have installed some audio/visual files with this command:

sudo apt-get install libxine-extracodecs ffmpeg lame faad sox mjpegtools gxineplugin flashplugin-nonfree

Do I need other codecs? Can I install Automatix in Xubuntu?

---

### Post by deeZee on 2007-05-23
HI, there.  For general DVD playback you'll need to install the libdvdread3 package.  To play encrypted DVD'S you'll also need to install the libdvdcss2 package.  You can get libdvdread3 by typing the following:```
sudo apt-get install libdvdread3
```  There are three different ways of installing libdvdcss2, depending on your version of Xubuntu (dapper, edgy, or feisty). Here are the instructions for each: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-e3dafb305e64ec576176ee706e287bb4d839cb12](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-e3dafb305e64ec576176ee706e287bb4d839cb12)
If you are using Feisty you'll also need the libxine1-ffmpeg package, which can be installed using sudo apt-get.  Hope this helps:)

---

### Post by geovino on 2007-05-24
Thanks, I was able to install Automatix for Xubuntu and installed the codecs that way. I'll keep these instructions for future installs.

---

