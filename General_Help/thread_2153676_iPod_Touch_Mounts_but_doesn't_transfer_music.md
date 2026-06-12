---
title: "iPod Touch Mounts but doesn't transfer music"
date: 2013-06-11
forum: General Help
---

### Post by bassclef on 2013-06-11
I'm running Ubuntu 12.04 and have had iPod trouble ever since I (double) upgraded from 11.04 to 12.04. Before I used gtkpod for transferring my music to my iPod nano, but now I'm using an iPod touch and gtkpod hasn't worked properly since I upgraded my OS. Gtkpod no longer recognizes .wav files and can barely handle only certain .mp3 files. Please help!

---

### Post by ubuntu27 on 2013-06-12
Did you try to do a clean install of Ubuntu or did you do a direct upgrade?

Try installing the following as well.
```
sudo apt-get install ifuse libgpod4 libimobiledevice-utils usbmuxd gnupod-tools
```

Also try to experiment by creating a new user, and then transferins music. See if it works.

---

