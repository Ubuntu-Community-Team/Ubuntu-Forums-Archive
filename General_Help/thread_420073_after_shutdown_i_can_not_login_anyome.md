---
title: "after shutdown i can not login anyome"
date: 2007-04-23
forum: General Help
---

### Post by mitjab on 2007-04-23
I upgrade ubunty to feisty and then computer shut down becouse lost power. Now i can not login to ubunty any more. I try with live cd but do not know how i can continue upgrading.

Any idea?
Thx

---

### Post by dannyboy79 on 2007-04-23
when you say you can't login  anymore, can you please be more specfic? is it at least booting all the way up and giving you gdm? (login screen) then it's just not accepting your username? i would suggest booting to the livecd and chrooting into you hard drive install. here are some suggestions. [http://ubuntuforums.org/showthread.php?t=417116&highlight=chroot+from+livecd](http://ubuntuforums.org/showthread.php?t=417116&highlight=chroot+from+livecd)

---

### Post by mitjab on 2007-04-23
```

Recommended packages:
  aptitude-doc-en aptitude-doc gdeb openoffice.org-mimelnk latex-xft-fonts
  libxine1-ffmpeg videolan-doc
The following packages will be REMOVED:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier
  adept-updater apt-index-watcher debtags
The following NEW packages will be installed:
  libgl1-mesa-glx libpoppler1-qt libpulse0
The following packages will be upgraded:
  apt aptitude gnome-apt hal kcontrol kdebase-data kicker kivio kivio-data
  koffice-data koffice-libs krita krita-data libdvdnav4 libkonq4 libpoppler1
  libpoppler1-glib libruby1.8 libxcomposite1 libxine-dev libxine1 vlc vlc-nox
23 upgraded, 3 newly installed, 9 to remove and 1111 not upgraded.
241 not fully installed or removed.
Need to get 0B/66.5MB of archives.
After unpacking 2945kB of additional disk space will be used.
Do you want to continue [Y/n]? y
apt-extracttemplates: error while loading shared libraries: libapt-pkg-libc6.4-6 .so.3.53: cannot open shared object file: No such file or directory
debconf: apt-extracttemplates failed: Bad file descriptor(Reading database ... 2 45807 files and directories currently installed.)
Unpacking libgl1-mesa-glx (from .../libgl1-mesa-glx_6.5.2-3ubuntu7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu7_i3 86.deb (--unpack):
 error creating symbolic link `./usr/lib/libGL.so.1': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

bz chroot i can login to mz ubuntu but i get this error. What to do.

Thx

---

### Post by dannyboy79 on 2007-04-23
did you do an update and then an upgrade? try to use the -F option to force aptitude to fix package dependency issues. if aptitude is giving you a specific name, than try to remove that package and then force an install of it.

---

### Post by the_olo on 2007-05-15
> dpkg: error processing /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu7_i3 86.deb (--unpack):
 error creating symbolic link `./usr/lib/libGL.so.1': No such file or directory

I think this is a problem with an ATI or NVidia binary driver deb package that didn't clean up its diversions after itself.

Try removing the ATI or Nvidia driver, then remove the diversions like this and tell me if it fixes your problem:

```
dpkg-divert --remove /usr/lib/libGL.so.1
dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
```

---

