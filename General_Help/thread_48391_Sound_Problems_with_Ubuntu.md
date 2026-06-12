---
title: "Sound Problems with Ubuntu"
date: 2005-07-12
forum: General Help
---

### Post by young_digital on 2005-07-12
i have been installing new stuff on ubuntu since i got it...am a newbie so i been using synaptic instead of apt-get...but i cant seem to have my system play sound....i use gxine to play cd's and that works just fine but i cant play mp3s...i downloaded vlc...and it seems to be playin but theres no sound comin out of the speakers....same thing with mpeg files.....it shows the video but wont play sound.....and whenever i try to play mp3 or wav files on xmms, the xmms program freezes.
im gettin really sick of this thing i was up all yesterday tryin to fix it but i cant seem to get help anywhere ...ive googled my life out for this to get fixed still no results.

can someone pls help me out with this???

---

### Post by runenes on 2005-07-12
Have you looked at the ubuntu guide: [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#codecs](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#codecs)

---

### Post by Norrad on 2005-07-12
I'm having exactly the same problem  ](*,)

---

### Post by manicka on 2005-07-12
Just follow the guide that the link above takes you to, to install the codecs and all should be well :D

---

### Post by Norrad on 2005-07-12
Going to give it a try but apt-get can't find some of those codecs. w32codecs and libdivx4linux etc. Most of the others it installs fine though  :neutral:

---

### Post by drummer on 2005-07-12
make sure that you have the extra repositories enabled first:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Norrad on 2005-07-12
Thanks, going to give it a try as soon as I get home  :)

---

### Post by young_digital on 2005-07-12
gave it a try but still didnt work....apt-get could not find these packages

gstreamer0.8-lame
w32codecs
libdivx4linux
lame
mjpegtools

or it said they did not have an installation candidate

more help will be appreciated.

---

### Post by young_digital on 2005-07-12
ive aded the repositories....and all the codecs for multimedia installed just fine but after that i tried to install mplayer so i can play my mp3 files smoothly with no problem but i get these error messages

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb)  MD5Sum mismatch

now ive seen another website that has these files fopr download....how can i configure apt-get to download these files from the new website and apply it to my mplayer installation?? is that possible with ubuntu??

---

### Post by arunsub on 2005-07-12
Download the codecs from here and install
[http://www.mplayerhq.hu/homepage/design7/dload.html#codecs](http://www.mplayerhq.hu/homepage/design7/dload.html#codecs)

---

