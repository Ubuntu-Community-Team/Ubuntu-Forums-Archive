---
title: "WINE crashes...hit audio by accident and I got"
date: 2007-04-21
forum: General Help
---

### Post by beachreader on 2007-04-21
WINE crashes...hit audio by accident and I got 

beachreader@beachreader:~$ winecfg
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serialto 0


any suggestions please I whole saturday is ruined....

:)

---

### Post by Robvdl on 2007-04-21
This is a common problem if you install wine, hit the audio tab in winecfg, it crashes. to fix I normally do this:

mkdir -p $HOME/.kde/socket-`hostname`
sudo apt-get install libjack0.100.0-dev

start winecfg again, click the audio tab untick "OSS", then tick "ALSA" and apply changes.

---

### Post by beachreader on 2007-04-22
thanks !!! that fixed one of my problems!! thanks again..

---

