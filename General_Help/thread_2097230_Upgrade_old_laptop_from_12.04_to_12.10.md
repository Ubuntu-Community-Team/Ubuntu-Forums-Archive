---
title: "Upgrade old laptop from 12.04 to 12.10?"
date: 2012-12-22
forum: General Help
---

### Post by simonj12 on 2012-12-22
Got a knackered old relic of a compaq nx6110. It runs 12.04 fine for what I want to use it for ie web browsing and a few other odds and ends. But I'm getting a bit bored and I'm wondering whether to bother upgrading to 12.10. I have an Intel celeron M and 768 Meg ram. Will 12.10 try to hog resources I haven't got and grind me to a halt? I have nothing of note to backup.

---

### Post by snowpine on 2012-12-22
Test drive a Live DVD/USB is my advice.

12.04 is fully supported through April 2017 so there is really no rush to upgrade in my opinion. :) If you're having trouble with outdated hardware then Xubuntu or Lubuntu are definitely worth a look.

---

### Post by simonj12 on 2012-12-23
Thanks. I'll give the usb stick a go. I've tried xubuntu on this laptop before and surprisingly it doesn't perform as well as ubuntu: occasional screen freezes and hanging. I might try lubuntu as well.

---

### Post by 3rdalbum on 2012-12-23
12.10 does not have Unity 2d, only the normal 3d Unity. If you have no 3d, or only reverse-engineered video support, you will see significant slowdown on 12.10 which can only be partly improved.

If you currently use Unity 3d on 12.04 with okay performance, then you can upgrade without a worry.

---

### Post by Yellow Pasque on 2012-12-23
You're in for some hassle if you do upgrade (even using Lubuntu). No 12.10 versions of buntu support non-PAE kernel by default. You'll have to hack around it since your pentium/celeron m doesn't have it: [http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html)

---

### Post by kleenex on 2012-12-23
Hi **simonj12**. You have written, that you have a 768 MB of RAM memory. You also wrote that Ubuntu run okay, but Xubuntu doesn't perform as well as Ubuntu. Are you trying to say, that 768 MB of RAM memory is enough for GNOME 3? I always thought that ~1 GB is not enough.

When it comes to your question - I'm suggesting you VirtualBox for trying Ubuntu 12.10. It is available in 12.04 and runs pretty good.

---

