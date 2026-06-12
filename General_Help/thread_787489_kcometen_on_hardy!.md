---
title: "kcometen on hardy?!"
date: 2008-05-08
forum: General Help
---

### Post by iwallet on 2008-05-08
the screen saver kcometen, is it possible to have this on the latest ubuntu (8.04) ? 
i would really like it!!!

---

### Post by iwallet on 2008-05-16
bump

---

### Post by maloo on 2008-06-15
Hi Ive just installed this to a somewhat fresh install of kubuntu 8.04. (just realised your using ubuntu, see note below)

1) Make sure you have the proprietary graphics drivers installed. My card was a Nvidia 7600, one of my mates had problems with an ati card, but this was a few years ago.

2) Download the source file from [HTML]http://www.kde-apps.org/content/show.php?content=30313&forumpage=11&PHPSESSID=e5af[/HTML]

3) I then installed quite a number of packages, some im sure are not needed such as the extra screensavers, but im still going to mention them since they could have effected the install process. Anyway in the terminal enter:
```
sudo apt-get install build-essential kdebase-dev kscreensaver-xsavers libxcb-screensaver0 kscreensaver-xsavers-extra rss-glx
```

4)untar the kcometen package and cd into the dir. Assuming the package was downloaded to the desktop enter the following in the terminal:
```
cd ./Desktop
tar -xvvzf kcometen3-1.1.tar.gz
cd ./kcometen3-1.1
```

5) Configure, make and install. Enter the following into the terminal:
```
./configure --prefix="/usr"
make
sudo make install
```

6) Kcometen should show up in the kde screensaver selection under opengl screensavers

I just realised you said you are using ubuntu. The basic procedure would be the same however you probably will need other build packages. If you skip step 3 and just run the configure script it should tell you what is required (with a bit of googling). Sorry about the pretty useless post, maybe this will help someone else out thou.

Paul

---

