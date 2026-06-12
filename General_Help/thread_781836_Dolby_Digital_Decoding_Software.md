---
title: "Dolby Digital Decoding Software"
date: 2008-05-04
forum: General Help
---

### Post by cadcrazy on 2008-05-04
I have M-Audio Revolution Sound card + Logitech x540 speakers. I don't have hardware based dolby digital decoder to play 5.1 DVD videos. In windows job is done by PowerDVD with  built in decoder. Does something similar exist for Linux. May be some plugin for vlc player or so

Thanks

---

### Post by jocko on 2008-05-04
You don't need any specific plugin to get vlc to decode dolby digital, it has it's own codec already included.

For other applications you may need to install the package "ubuntu-restricted-extras"

In mplayer (gui version), select preferences --> Codecs and demuxer and in the "audio codec family" select "AC3/DTS decoding with liba52".
In mplayer (no gui), add this line to /home/yourname/.mplayer/config:
```
afm=a52,
```

---

### Post by cadcrazy on 2008-05-04
I tried to play 5.1 dvd's on vlc player in windows as well as in Ubuntu. I doubt there is no dolby digital decoder in VLC. May be i have to change some option. I'll try it in mplayer but personally i don't like mplayer over VLC.

---

### Post by jocko on 2008-05-05
> **cadcrazy said:**
> I tried to play 5.1 dvd's on vlc player in windows as well as in Ubuntu. I doubt there is no dolby digital decoder in VLC. May be i have to change some option. I'll try it in mplayer but personally i don't like mplayer over VLC.

Trust me, I can play dvds and movie files with ac3 sound on my laptop in both mplayer and vlc, and both decodes dolby digital and dts and gives me analog sound through the speakers, with their own liba52 codecs. Check the options in vlc and make sure it's *not* set to use spdif but is set to detect dolby digital.

---

