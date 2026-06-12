---
title: "DVD won't play on xenial desktop"
date: 2016-09-28
forum: General Help
---

### Post by ineuw on 2016-09-28
All restricted software is installed, including libdvdread4 and libdvdcss.py but the DVD video won't play. I  use Videolan and it's a commercially released show which plays on Windows 7 without any problems. What am I missing?

---

### Post by #&amp;thj^% on 2016-09-28
[s]Is this on a Tower PC or a Macbook?[/s] Never mind just seen the windows 7 in your post.:D

```
sudo apt install libdvd-pkg libdvdread4
```

and follow on-screen directions.


> In some countries, the use of the below unlicensed decryption software is not permitted by law. Verify that you are within your rights to use it.
Others have had better luck with this method:
1. Open terminal. When it opens, paste the command below and hit run to install libdvdread and other required codecs:

```
sudo apt install libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg

```

---

### Post by ineuw on 2016-09-28
My thanks. The first option worked. BTW, the DVD is borrowed from the Government library. Also, it worked fine before upgrading from Xu 14.04 to Xu 16.04.

---

