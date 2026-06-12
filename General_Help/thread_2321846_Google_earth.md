---
title: "Google earth"
date: 2016-04-24
forum: General Help
---

### Post by peter228 on 2016-04-24
Is there a preferred way of installing Google Earth in Ubuntu 16.04?

---

### Post by HereInOz on 2016-04-25
G'Day,

This could be what you are looking for:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Not specifically for 16.04 but it should work.

---

### Post by jim_deadlock on 2016-04-25
16.04 is missing lsb-core which is causing all kinds of problems with GE. I've managed to do it by manually installing 3 dependencies manually as described here:

[URL="https://ubuntu-mate.community/t/install-google-earth-on-ubuntu-16-04/5268"]https://ubuntu-mate.community/t/install-google-earth-on-ubuntu-16-04/5268
[/URL]
They show as 15.10 versions but work fine. eg:

```
sudo apt-get install ./lsb-core_4.1+Debian11ubuntu8_amd64.deb
```

They may throw up errors saying "Can't drop privileges for downloading as file" but that can be ignored since they install despite the error. Once the 3 dependencies are installed just download/install GE as usual.

---

### Post by peter228 on 2016-04-25
Thanks for the comments.   Sounds a bit like I may have to wait a bit.

I know with 14.04 I had problems with pictures not loading from markers but there was a workaround from a guy I think in India ...  I was hoping that all may have been fixed now but it sounds a bit like getting it running is an achievement, having it work correctly may be nice.

---

### Post by jim_deadlock on 2016-04-25
Well having installed as above, the panoramia (pictures) thing is indeed fixed at least :D

---

### Post by peter228 on 2016-04-25
very good to hear that ....

---

### Post by peter228 on 2016-05-02
I followed the instructions at this link
[http://skagitsignal.com/?p=1740](http://skagitsignal.com/?p=1740)

Google Earth is installed but the old problem of pictures not displaying is back ... all I get is the window with a white background.

---

### Post by jim_deadlock on 2016-05-02
I spoke too soon before, it seems that the gold icons do show the pictures but the normal ones don't.

Update: fixed here: [http://www.sundru.net/wordpress/tech-stuff/google-earth-on-ubuntu-16-04-xenial-xerus/](http://www.sundru.net/wordpress/tech-stuff/google-earth-on-ubuntu-16-04-xenial-xerus/)

---

