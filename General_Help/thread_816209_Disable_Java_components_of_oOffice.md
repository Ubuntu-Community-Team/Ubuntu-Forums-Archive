---
title: "Disable Java components of oOffice"
date: 2008-06-02
forum: General Help
---

### Post by dlublink on 2008-06-02
hello,

I was reading today that OpenOffice uses a lot of memory because of the java components. In my own comparisons I found that in one case Word took 2 megabytes ( with a 10 page file with a lot of small images ) to run and OpenOffice took 58 megabytes to open an empty document.

How do I disable the java components of OpenOffice?

Thanks,

David

---

### Post by ibuclaw on 2008-06-02
As far as I'm aware, all java scripts/components for OpenOffice are in the package **openoffice.org-java-common** that can be found in synaptic.

If the package is installed, you may consider removing it (As tt isn't installed by default in Ubuntu).

Although, there is a package called **openoffice,org-gcj** which (reading from package info) "*compiles to native to make the java features of OOo faster*"

Either option may see an improvement in what your seeing.

Regards
Iain

---

### Post by dlublink on 2008-06-02
Unfortunately that doesn't work, it tells me that everything will be removed :
```

root@david-desktop:/home/david# apt-get remove openoffice.org-java-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwildmidi0 libavutil1d libdc1394-13 libxvidcore4 libsoundtouch1c2 mplayer-skins libotr2 libwxgtk2.6-0 lightning-extension libsvga1 libflashsupport audacity mplayer libopenspc0
  kismet libflac++6 libpostproc1d libsnack2 libavformat1d libx264-57 gstreamer0.10-ffmpeg libenca0 libgmp3c2 compizconfig-settings-manager python-compizconfig libggi2 libgii1
  libwxbase2.6-0 tcltls rar libgii1-target-x libgsm1 libdvdnav4 gstreamer0.10-plugins-bad flashplugin-nonfree tcl8.5 libcdaudio1 mozilla-mplayer libxvmc1 tk8.5 liblua5.1-0 mpg123
  libavcodec1d libgmyth0 openvpn libadns1 lame liblame0 openvpn-blacklist wireshark-common libiptcdata0 libfaac0 libfaad0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  openoffice.org openoffice.org-base openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-java-common openoffice.org-officebean openoffice.org-writer2latex
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 12.9MB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by ibuclaw on 2008-06-02
Not exactly true.

[LIST]
[*]**openoffice.org** is just a meta-package linking everything (not installed by default to save disk space).
It contains no data in it, so nothing lost.
[*]**openoffice.org-base** is not required. All the main components are inside the package named **openoffice.org-base-core**.
[*]I can see you having no use for **filter-mobiledev**, **officebean** or **writer2latex**. So we can safely ignore the sight of those packages.
[/LIST]

Which just leaves us with the evolution plugin...

If you don't use evolution with OpenOffice, it should be alright to remove all dependancies.

Also, those packages set to autoremove, won't be removed...

Although you should consider unmarking them:
```
sudo apt-get install libwildmidi0 libavutil1d libdc1394-13 libxvidcore4 libsoundtouch1c2 mplayer-skins libotr2 libwxgtk2.6-0 lightning-extension libsvga1 libflashsupport audacity mplayer libopenspc0 kismet libflac++6 libpostproc1d libsnack2 libavformat1d libx264-57 gstreamer0.10-ffmpeg libenca0 libgmp3c2 compizconfig-settings-manager python-compizconfig libggi2 libgii1 libwxbase2.6-0 tcltls rar libgii1-target-x libgsm1 libdvdnav4 gstreamer0.10-plugins-bad flashplugin-nonfree tcl8.5 libcdaudio1 mozilla-mplayer libxvmc1 tk8.5 liblua5.1-0 mpg123 libavcodec1d libgmyth0 openvpn libadns1 lame liblame0 openvpn-blacklist wireshark-common libiptcdata0 libfaac0 libfaad0
```

Regards
Iain

---

### Post by dlublink on 2008-06-02
I either use webmail or thunderbird. I don't use evolution so that is not a loss.

I will try and remove the said packages and mark the others as keepers.

Thanks!

David

---

### Post by dlublink on 2008-06-02
I removed the java components and relaunched openoffice, it still takes a significant amount of memory. 55 megabytes with a blank document. I won 3 megabytes, but I wonder if this is because memory usage varies. It just seems like so much memory consumption for nothing. Office 2003 on Windows XP takes about 2 megabytes ( on the test I did yesterday ). It really frustrates me that OpenOffice is so resource hungry. My sister used my computer Saturday and OpenOffice was crashing every 10 minutes because it was eating up too much memory.

On a lighter note, I got significant performance boost by installing the FlashBlock plugin into firefox. Before this plugin was installed, my computer would run at a snails pace when I had more than 5 tabs open. With this installed, Firefox is a lot faster and less resource hungry. Since there are very few websites that use flash for something other than showing me ads, this is really a great plugin.

---

