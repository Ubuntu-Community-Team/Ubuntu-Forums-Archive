---
title: "Total crash - I think due to wifi driver"
date: 2014-01-19
forum: General Help
---

### Post by Phear46 on 2014-01-19
Hi guys, upon re-installing Ubuntu I'm having a serious issue which I believe is being caused by my WiFi card. It was previously working, and I'm not sure how I got it to work before, I don't seem to be able to find the instructions anywhere.

I've tried installing while connected to the net and auto-downloading updates, I've tried without updates, I've tried various ways of installing the drivers. All end in the same result, random total crashes within a few mins of boot.

I'm 99% sure its due to the WiFi card, although I'm not all all sure why its going this wrong. I think I need to totally remove the WiFi drivers and start over but I'm not sure how at this point.
The card is a BM4318 I believe. There is loads of info on the net about this card not working correctly but nothing like what I'm experiencing. And it WAS working fine before a re-install.

Im using 12.04, which is the same as before.


Heres the screen im left with:
[[IMG]http://s30.postimg.org/c7scxxjst/IMAG0195.jpg[/IMG]]("http://postimg.org/image/c7scxxjst/")


[[IMG]http://s30.postimg.org/kky1slj0d/IMAG0198.jpg[/IMG]]("http://postimg.org/image/kky1slj0d/")


[[IMG]http://s30.postimg.org/82hgc0m0t/IMAG0199.jpg[/IMG]]("http://postimg.org/image/82hgc0m0t/")

Sorry its over 3 images, my camera doesn't seem to be able to grab the whole thing without distorting the text in places.

Any ideas? If any more info is required let me know.

Thanks,
Nathan

---

### Post by Phear46 on 2014-01-19
Solved! (I hope)

Ok, it seems that ubuntu wants to install the bcmwl-kernel-source package as default (this i belive is the restriced drivers package). This is causing the problem.

What i did:

```
dpkg -r bcmwl-kernel-source

dpkg -P bcmwl-kernel-source

apt-get install b43-fwcutter

modprobe b43 (not sure this did anything, no idea what mod probe does)
```

reebooted
```

apt-get install firmware-b43-installer
```

reebooted and boom, seems rock solid! I think the trick was to remove and purge the bcmwl package before the crash. Seemed to be stable after that.

---

