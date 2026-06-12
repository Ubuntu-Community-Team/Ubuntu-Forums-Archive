---
title: "Streaming Video problem"
date: 2008-06-06
forum: General Help
---

### Post by rated_emman on 2008-06-06
i tried to watch a streaming video... and i get this error:

The playback of this movie requires a Advanced Streaming Format (ASF) demuxer plugin which is not installed.

what should i do?

---

### Post by pressed on 2008-06-20
*bump

---

### Post by iaculallad on 2008-06-20
Add the Medibuntu Repository:

For Ubuntu 7.10 "Gutsy Gibbon":

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

For Ubuntu 8.04 "Hardy Heron":

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Add the GPG Key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Install mplayer if not installed on your sytem:

```
sudo apt-get install mplayer
```

Install the W32Codec components:

```
sudo apt-get install w32codecs
```

Once all installation are finished, Goto Applications->Sound and Video, select "MPlayer Movie Player", right-click on the window that appear and select "Open" -> Play URL and enter your HTTP address.

---

### Post by khalidmian on 2009-01-06
The following packages have unmet dependencies:
  mplayer: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
           Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
           Depends: libjack0 (>= 0.109.2) but it is not going to be installed
           Depends: libmad0 (>= 0.15.1b-3) but it is not going to be installed
           Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
           Depends: libspeex1 (>= 1.2~beta3-1) but 1.1.12-3ubuntu0.8.04.1 is to be installed
E: Broken packages


Please help

---

