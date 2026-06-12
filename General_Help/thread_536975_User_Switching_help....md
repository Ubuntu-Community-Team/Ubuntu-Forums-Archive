---
title: "User Switching help..."
date: 2007-08-28
forum: General Help
---

### Post by vanden12 on 2007-08-28
Well here the thing...

I want to use Switching User but when I do it in the ubuntu shutdown menu my mouse stops working....It only works when i close the laptop for a few secs and goes into locking screen from there I can do to Switching User...If I do it any other way my mouse just to stop working..


It a  Toshiba Laptop with 7.04...Help?

---

### Post by bobbybobington on 2007-08-28
This seems to be a fairly common problem and there is a *temporary* workaround and try at your own risk. The developers are working on it right now, so I hope it'll be fixed by Gutsy.
1)```
 apt-get source xserver-xorg-input-synaptics
```

2) ```
wget http://launchpadlibrarian.net/8354070/patch
```

3) ```
patch -p0 < patch
```

4) ```
sudo apt-get build-dep xserver-xorg-input-synaptics
```

5) ```
cd xserver-xorg-input-synaptics*
```

6) ```
sudo dpkg-buildpackage
```

7) ```
cd ..
```

8) ```
sudo dpkg -i xserver-xorg-input-synaptics*.deb
```

---

### Post by vanden12 on 2007-08-28
Might it be fixed in 7.10..?

---

