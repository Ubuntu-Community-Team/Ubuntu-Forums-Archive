---
title: "How do I tell the update manager to ignor a package?"
date: 2006-12-08
forum: General Help
---

### Post by TheEremite on 2006-12-08
I compiled and installed a few packages from source... ffmpeg and the included libavcodec0d libavcodec-dev and libavformat-dev.

I wanted to have mp3 and xvid support, and I guess the normal ubuntu ffmpeg has disabled them. Anyway, it works great now but the software updater thinks that the packages in the ubuntu repo are newer versions... which is weird because the versions are the same number. So, is there a way to tell the updater that these are actually newer than the ones in the repo?

thanks.


edit:
umm... please *ignore* my misspelled title :/

---

### Post by 23meg on 2006-12-08
Choose the package in Synaptic and hit Package / Lock Version .

---

### Post by TheEremite on 2006-12-08
It doesn't seem to want to let me

I select the "lock version" box, it reloads the list and the box is no longer checked when I go pack to the package menu... and update manager still wants to install it.

---

### Post by bodhi.zazen on 2006-12-08
```
sudo echo "package_name hold"|dpkg --set-selections
```

Where "package_name" is the name of the package to put on hold, example:
sudo echo "wine hold"|dpkg --set-selections

To release:```
sudo echo "package_name install"|dpkg --set-selections
```

example:
sudo echo "wine install"|dpkg --set-selections

---

### Post by TheEremite on 2006-12-10
Fantastic. That worked great.

Thank you

---

