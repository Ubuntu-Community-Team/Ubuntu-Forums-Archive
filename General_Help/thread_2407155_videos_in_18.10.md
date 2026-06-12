---
title: "videos in 18.10"
date: 2018-11-30
forum: General Help
---

### Post by hmiersch on 2018-11-30
hi.
i recently updated to 18.10, and now i can't find the videos app. where is it? 
for now, i've installed VLC, but the UI SUCKS. but hey, under 18.04 VLC was totally unusable, so i guess thats an improvement...

---

### Post by howefield on 2018-11-30
The default video player package is removed from a minimal install of Ubuntu but should be present in a standard "full" install.

Try the following in terminal..

```
apt-cache policy totem
```

---

### Post by hmiersch on 2018-11-30
> **howefield said:**
> The default video player package is removed from a minimal install of Ubuntu but should be present in a standard "full" install.

i thought i'd done a full install. did i screw up?

> 

Try the following in terminal..

```
apt-cache policy totem
```

no sudo. so it should work in my user account. i'll give it a go. 

update: it worked. here is what it gave me: 

totem:
  Installed: (none)
  Candidate: 3.26.2-1ubuntu2
  Version table:
     3.26.2-1ubuntu2 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) cosmic-updates/main amd64 Packages
     3.26.2-1ubuntu1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) cosmic/main amd64 Packages

---

### Post by howefield on 2018-11-30
Looks like it isn't installed, so *sudo apt install totem* should do it.

---

