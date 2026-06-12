---
title: "Opera after update to version 42 lost support for h.264"
date: 2016-12-21
forum: General Help
---

### Post by GanJ on 2016-12-21
In Opera 41 all works fine, but after update to Opera 42 support for h.264 was broken

Is it a opera bug or something wrong with my setup? 

Are there anybody who has issue like me

Ubuntu 16.04 LTS, Opera [COLOR=#0A0A0A][FONT=Arial]42.0.2393.94. 

[/FONT][/COLOR]

[IMG]http://i.imgur.com/t9V3CgP.png[/IMG]

---

### Post by Frogs Hair on 2016-12-21
I see the same and would think it's a browser problem.

---

### Post by wyth on 2017-01-02
Noticed the same thing. I've been looking for an answer for a day or so, and this is the first post I've seen related to the issue. Kinda strange.

---

### Post by Frogs Hair on 2017-01-02
Same with the beta and developer versions. I know opera was sold and some key people have jumped ship, but can't say if it's related.

---

### Post by mc4man on 2017-01-02
Due to licensing it's been dropped (they didn't or can't pay
To return - 
Get latest or current  chromium-codecs-ffmpeg-extra package (install & grab from /var/apt/archives or go to [ubuntu packages page]("http://packages.ubuntu.com/xenial-updates/chromium-codecs-ffmpeg-extra")
Extract it > inside extract the data.tar.xz file > navigate to  usr/lib/chromium-browser.
Inside is libffmpeg.so  copy it & replace /usr/lib/x86_64-linux-gnu/opera/libffmpeg.so with it (location is for 64 bit installs
screens show

---

### Post by mrai on 2017-01-06
Thanks. I was looking for the same thing. Your workaround works!

---

