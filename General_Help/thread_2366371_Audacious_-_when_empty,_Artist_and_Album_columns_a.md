---
title: "Audacious - when empty, Artist and Album columns are filled in with the folder name"
date: 2017-07-17
forum: General Help
---

### Post by ardouronerous on 2017-07-17
I'm running Audacious 3.6.2, and I'm experiencing this bug:

[http://redmine.audacious-media-player.org/issues/661](http://redmine.audacious-media-player.org/issues/661)

The solution according to the bug report is to unchecked the "guess missing metadata" option, but I can't find this option.

---

### Post by Dennis N on 2017-07-17
"Guess missing metadata..." is found here:

File > Settings > Song Info > Advanced > Guess missing metadata from file path (check box)

---

### Post by ardouronerous on 2017-07-17
> **Dennis N said:**
> "Guess missing metadata..." is found here:

File > Settings > Song Info > Advanced > Guess missing metadata from file path (check box)

No advanced settings found on Song Info:
[ATTACH=CONFIG]276028[/ATTACH]

---

### Post by Dennis N on 2017-07-17
Apparently that section was added at some point to later versions of Audacious. See screen shot. As an alternative, why not fill the empty field with "Unknown" or "n/a" (not available) when you don't have the information?

---

### Post by ardouronerous on 2017-07-17
Too many mp3s to edit lol

Okay, so I guess I'll have to wait til Xubuntu 16.04 LTS updates Audacious to higher versions then.

Thanks for the info :)

---

### Post by Dennis N on 2017-07-17
The Advanced Options section starts appearing in Audacious 3.7 series. Latest Ubuntu release (17.04) uses this version.

---

### Post by #&amp;thj^% on 2017-07-17
Or if you don't mind adding a PPA you can get 3.8 Stable...I've been running it for just short of a year now.
Also now supports ability to run multiple instances of Audacious.
How to Install Audacious 3.8 Stable in Ubuntu 16.04
[http://ubuntuhandbook.org/index.php/2016/09/install-audacious-3-8-stable-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/09/install-audacious-3-8-stable-ubuntu-16-04/)
```
$ apt policy audacious
audacious:
  Installed: 3.8.2-1~webupd8~xenial0
  Candidate: 3.8.2-1~webupd8~xenial0
  Version table:
 *** 3.8.2-1~webupd8~xenial0 100
        100 /var/lib/dpkg/status
     3.6.2-2 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```

---

