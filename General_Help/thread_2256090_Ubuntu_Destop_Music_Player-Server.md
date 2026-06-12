---
title: "Ubuntu Destop Music Player-Server"
date: 2014-12-09
forum: General Help
---

### Post by pablolie on 2014-12-09
Is there a way to make an Ubuntu Desktop machine play my music library while controlled from a device like an iPad or a PC?

Basically I want a nice user interface for music playing. The (old, cheap) Ubuntu Desktop laptop would mostly be hidden away, connected to a DAC that in turn connects to my amplifier. The laptop would also host the music library. I know how to set up a Linux volume so it's shareable (Samba is your friend).

Can that be done with some software package? I could do that on a PC with JRiver Media Center, not sure if there's similar stuff in Ubuntu.

---

### Post by tgalati4 on 2014-12-09
You could run *[mpd]("https://help.ubuntu.com/community/MPD")* on the Ubuntu machine and use one of several mpd clients to control it.

Open a terminal:

```
apt-cache search mpd
```

---

