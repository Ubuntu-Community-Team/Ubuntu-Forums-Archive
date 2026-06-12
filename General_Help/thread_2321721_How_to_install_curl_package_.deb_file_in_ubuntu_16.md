---
title: "How to install curl package .deb file in ubuntu 16.04?"
date: 2016-04-24
forum: General Help
---

### Post by james_connor on 2016-04-24
[COLOR=#111111][FONT=Ubuntu]I download curl deb file from curl official site : [https://curl.haxx.se/](https://curl.haxx.se/). I want to install curl deb file but meet this trouble: [http://imgur.com/a/A8zQi](http://imgur.com/a/A8zQi)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Please tell e how to fix this trouble. I'm not edit anything on /etc/apt/sources.list. Why this trouble happend to me?[/FONT][/COLOR]

---

### Post by slickymaster on 2016-04-24
*Thread moved to **General Help**.*

The curl package is in the repos```
sudo apt-get install curl
```

---

### Post by nothingspecial on 2016-04-24
```
sudo apt-get install -f
```

---

