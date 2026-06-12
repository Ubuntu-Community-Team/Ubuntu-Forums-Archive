---
title: "Ubuntu Package manager broken"
date: 2013-05-26
forum: General Help
---

### Post by saniyauzumaki on 2013-05-26
I installed some packages at this site to install [MLT ]("http://kevin.deldycke.com/2010/11/latest-stable-kdenlive-development-version-mlt/") 
and later on i found out that my package manager is broken!
Iam beginner at using ubuntu and have dont idea what to do
The error message is error:Brokencount>0



Here is the output of the image
The following packages have unmet dependencies:

The following packages have unmet dependencies:


kdenlive: Depends: libc6 (>= 2.15) but 2.15-0ubuntu20 is installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.7.2-2ubuntu1 is installed
          Depends: libkdecore5 (>= 4:4.4.95) but 4:4.9.4-0ubuntu0.3 is installed
          Depends: libkdeui5 (>= 4:4.8.80) but 4:4.9.4-0ubuntu0.3 is installed
          Depends: libkio5 (>= 4:4.7.0) but 4:4.9.4-0ubuntu0.3 is installed
          Depends: libknewstuff3-4 (>= 4:4.4.0) but 4:4.9.4-0ubuntu0.3 is installed
          Depends: libknotifyconfig4 (>= 4:4.3.4) but 4:4.9.4-0ubuntu0.3 is installed
          Depends: libmlt++3 but it is not installed
          Depends: libnepomuk4 (>= 4:4.5.85) but 4:4.9.4-0ubuntu0.3 is installed
          Depends: libqt4-dbus (>= 4:4.6) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
          Depends: libqt4-opengl (>= 4:4.6) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
          Depends: libqt4-script (>= 4:4.6.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
          Depends: libqt4-svg (>= 4:4.6) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
          Depends: libqt4-xml (>= 4:4.6) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
          Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
          Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
          Depends: libsolid4 (>= 4:4.3.4) but 4:4.9.4-0ubuntu0.3 is installed
          Depends: libstdc++6 (>= 4.4.0) but 4.7.2-2ubuntu1 is installed
          Depends: kdenlive-data (= 0.9.6-0ubuntu0~sunab~quantal1) but 0.9.6-0ubuntu0~sunab~quantal1 is installed
          Depends: melt but it is not installed
          Depends: libmlt-data but it is not installed
openshot: Depends: melt but it is not installed
          Depends: python (>= 2.5) but 2.7.3-0ubuntu7 is installed
python-mlt5: Depends: libc6 (>= 2.4) but 2.15-0ubuntu20 is installed
             Depends: libgcc1 (>= 1:4.1.1) but 1:4.7.2-2ubuntu1 is installed
             Depends: libmlt++3 but it is not installed
             Depends: libpython2.7 (>= 2.7) but 2.7.3-5ubuntu4 is installed
             Depends: libstdc++6 (>= 4.1.1) but 4.7.2-2ubuntu1 is installed
             Depends: python (>= 2.7.1-0ubuntu2) but 2.7.3-0ubuntu7 is installed


Here is the screen shot  
[img]http://i1320.photobucket.com/albums/u532/saniyauzumaki/Screenshotfrom2013-05-26215047_zps94163150.png[/img]

---

### Post by claracc on 2013-05-26
What ubuntu release are you running?, the instructions you have followed to install MLT are for ubuntu 10.10.

It seems you have installed a lot of libraries with unmet dependencies.

If you have used a ppa repository for MLT installation, do as adviced and disable it, then run in a xterm:
```
sudo apt-get install -f
```

---

