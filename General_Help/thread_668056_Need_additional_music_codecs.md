---
title: "Need additional music codecs"
date: 2008-01-15
forum: General Help
---

### Post by NuNn DaDdY on 2008-01-15
What would be the repository/apt-get command that I need to get the necessary music codecs to play internet radio or what would be a good player to get so I would be able to play such files.

---

### Post by feistybird on 2008-01-15
Follow the repositories howto here :
[http://help.ubuntu.com/community/Medibuntu](http://help.ubuntu.com/community/Medibuntu)

install w32codecs and mozilla-mplayer plugin by paste the following line into terminal:

```
sudo apt-get install w32codecs mozilla-mplayer
```

Do this if you want to remove the default totem plugin:

```
sudo apt-get remove totem-mozilla
```

And go get a very helpful Firefox Add-On: Media Wrap:

[https://addons.mozilla.org/en-US/firefox/addon/1879](https://addons.mozilla.org/en-US/firefox/addon/1879)

---

