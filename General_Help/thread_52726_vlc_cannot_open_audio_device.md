---
title: "vlc: cannot open audio device"
date: 2005-07-28
forum: General Help
---

### Post by OneSeventeen on 2005-07-28
I am unable to play music or DVDs using VLC or MPlayer because it cannot open audio device.

They both default to /dev/snd

any tips?

---

### Post by rtrevor on 2005-07-28
For VLC try installing the 'vlc-plugin-esd' package

For mplayer, in console type 'sudo nano /etc/mplayer/mplayer.conf' and where it says "ao=alsa", change it to "ao=esd"

HTH,
-Roger

---

### Post by OneSeventeen on 2005-07-28
Well, I just finished following the guide at [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)
and the sound works fine now, but unfortunately I'm still having some other issues, but that's another thread :p

Thanks for the tip though!

---

