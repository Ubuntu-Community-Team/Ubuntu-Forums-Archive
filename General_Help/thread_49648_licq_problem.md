---
title: "licq problem"
date: 2005-07-17
forum: General Help
---

### Post by hideki on 2005-07-17
i have a really annoying problem with licq. the auto-away feature does not work! i am running hoary on amd64 and using the latest licq version installed via apt-get. i think it is 0.3-3. has anyone else experienced problems with non working auto-away? i already looked at the source and hoped to find something, but all i found was a reference to the xscreensaver libs. do i have a screensaver enabled for auto-away to work?

---

### Post by hideki on 2005-07-20
i have solved the problem myself with the help of the licq mailing list. i wrote a little post on my blog about it. so, if you are interested, here is the link:
[enter the nerdcave](http://blog.nerdcave.de/2005/07/issues-with-licq-under-ubuntu-hoary.html) 

quick summary:
```
sudo apt-get install libxss-dev
sudo apt-get build-dep licq
sudo apt-get source -b licq
dpkg -i licq*deb
```

---

