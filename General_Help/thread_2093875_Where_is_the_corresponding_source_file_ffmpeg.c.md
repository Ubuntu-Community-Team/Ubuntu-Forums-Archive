---
title: "Where is the corresponding source file ffmpeg.c ?"
date: 2012-12-12
forum: General Help
---

### Post by jiapei100 on 2012-12-12
Hi, all:

Environment: Ubuntu 12.10

I installed the default FFMPEG from the default repository of Ubuntu 12.10, say **6:0.8.4-0ubuntu0.12.10.1**
I'm also able to use the command "/usr/bin/ffmpeg". However, what I want to do is to see the source code of this command executive, namely, **ffmpeg.c** .

Where can I find the corresponding **ffmpeg.c** of this FFMPEG version, say **6:0.8.4-0ubuntu0.12.10.1** ?


Cheers
Pei

---

### Post by ororo on 2012-12-12
Do you mean this?

```
apt-get source ffmpeg
```

---

### Post by jiapei100 on 2012-12-12
Thank you so much... 
I found it at
> ./libav-0.8.4/ffmpeg.c

Thanks indeed. !!!

> **ororo said:**
> Do you mean this?

```
apt-get source ffmpeg
```

---

### Post by jiapei100 on 2012-12-15
Hi, Ororo:


```
sudo apt-get source ffmpeg
``` brings me libav 4:0.8.4:
> &#33719;&#21462;&#65306;1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates/main libav 4:0.8.4-0ubuntu0.12.04.1 (dsc) [3,692 B]
&#33719;&#21462;&#65306;2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates/main libav 4:0.8.4-0ubuntu0.12.04.1 (tar) [5,450 kB]
&#33719;&#21462;&#65306;3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates/main libav 4:0.8.4-0ubuntu0.12.04.1 (diff) [41.1 kB]

, which is probably exactly the same as the default package **libav-source** from the default repository of Ubuntu 12.04.


However, I've never successfully built **ffmpeg.c** . 
The problem I found is:
> **AVAudioConvert** has never been defined.



BTW, by doing ```
sudo apt-get source ffmpeg
```, where is the source code located?



Cheers
Pei


> **ororo said:**
> Do you mean this?

```
apt-get source ffmpeg
```

---

### Post by Cheesemill on 2012-12-15
You don't need to use sudo with 'apt-get source' as it doesn't install anything. It simply downloads the source code to your current directory.

---

