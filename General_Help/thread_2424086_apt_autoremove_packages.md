---
title: "apt autoremove packages"
date: 2019-08-03
forum: General Help
---

### Post by boris12 on 2019-08-03
Hello everyone! I am getting this message: 
```
The following packages were automatically installed and are no longer required:
  blender-data fonts-dejavu freepats gdal-data gstreamer1.0-nice
  gstreamer1.0-plugins-bad javascript-common libaec0 libarmadillo8 libarpack2
  libavdevice57 libblosc1 libboost-regex1.65.1 libcharls1 libcrypto++6
  libdap25 libdapclient6v5 libde265-0 libepsilon1 libepub0 libfarstream-0.2-5
  libfluidsynth1 libfreexl1 libfyba0 libgadu3 libgdal20 libgdcm2.8
  libgeos-3.6.2 libgeos-c1v5 libgeotiff2 libglew2.0 libgssdp-1.0-3
  libgtkmm-3.0-1v5 libgupnp-1.0-4 libgupnp-igd-1.0-4 libhdf4-0-alt libhdf5-100
  libinfgtk-0.7-0 libjemalloc1 libjs-jquery libjsoncpp1 libkf5khtml-bin
  libkf5khtml-data libkf5khtml5 libkmlbase1 libkmldom1 libkmlengine1
  liblilv-0-0 libllvm7 liblog4cplus-1.1-9 libmeanwhile1 libmediainfo0v5
  libmessaging-menu0 libminizip1 libmjpegutils-2.1-0 libmms0 libmodplug1
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 libnetcdf13 libnice10 libofa0 libogdi3.2
  libopenal-data libopenal1 libopencolorio1v5 libopencv-core3.2
  libopencv-imgcodecs3.2 libopencv-imgproc3.2 libopencv-videoio3.2
  libopenimageio1.7 libopenshot-audio6 libopenshot14 libopenvdb5.0 libpq5
  libproj12 libprotobuf-c1 libpurple-bin libpurple0 libqhull7 libqt5designer5
  libqt5help5 libsdl2-2.0-0 libserd-0-0 libsocket++1 libsord-0-0
  libsoundtouch1 libspatialite7 libspnav0 libsratom-0-0 libsrtp2-1 libsuperlu5
  libsz2 libtbb2 libtinyxml2-6 libtinyxml2.6.2v5 liburiparser1 libvo-aacenc0
  libvo-amrwbenc0 libwildmidi-config libwildmidi2 libxerces-c3.2
  libxml++2.6-2v5 libyaml-cpp0.5v5 libzbar0 libzen0v5 libzephyr4 libzip4
  net-tools pidgin-data proj-bin proj-data python3-openshot python3-pyqt5
  python3-pyqt5.qtsvg python3-pyqt5.qtwebkit python3-sip python3-zmq
Use 'sudo apt autoremove' to remove them.


```

Since I got problems with autoremove in the past , what is the safest way to deal with it?

Thank you in advance!

---

### Post by Artim on 2019-08-03
These are old library files and stuff, obsolete, just taking up valuable space.  What kind of problems have you had with autoremove, I wonder?

---

### Post by boris12 on 2019-08-03
I couldn't get into gnome desktop as far as I can remember. this incident happened 2 or 3 years ago.

---

### Post by yetimon_64 on 2019-08-03
> **Artim said:**
> These are old library files and stuff, obsolete, just taking up valuable space.  What kind of problems have you had with autoremove, I wonder?
On more than one occasion here using the autoremove switch has rendered my install non functional requiring a rebuild as repairs needed were just too extensive. It is possible to "behead" your desktop and end up booting to a CLI only install from my accidents with autoremove.

It is a handy tool but pay it respect, think carefully what you have changed in your system recently before blindly using autoremove; read the list of packages to be removed carefully first. That is a good way to see if you are about to render your install to a computing "stone age like" CLI boot.

> 
                         I couldn't get into gnome desktop as far as I can remember. this incident happened 2 or 3 years ago.         
In the last about 11 years, autoremove screw-ups have killed at least 3 desktop installations of mine usually leaving the installation booting to the console only.

**Question:** Have you by any chance uninstalled blender recently OP?
That list doesn't seem to be removing desktop related packages at a glance, more like stuff hauled in by the installation of something like blender.
**Edit**: > blender-data fonts-dejavu freepats ......seems a safe enough list to use autoremove with.

---

### Post by cruzer001 on 2019-08-03
What's the output of:
```
lsb_release -a
```

---

### Post by cruzer001 on 2019-08-03
And what have you removed lately?
 ```
cat /var/log/apt/history.log
```
or
```
grep "remove " /var/log/dpkg.log
```

---

### Post by Dennis N on 2019-08-03
'automatically installed' means they were installed as dependencies of other packages installed by apt. If at some point, when no package that apt knows about depends on them, they become candidates for autoremoval.

One problem I've seen is some program not installed by apt could also depend on one of these autoremove candidates. autoremove is unaware of those. Examples: some linux game, which are sometimes distributed as binaries; an application distributed as an AppImage; maybe snap packages? flatpacks?

So be careful.

---

### Post by Frogs Hair on 2019-08-03
If you have PPAs installed or Pre-released updates enabled use caution also.

---

### Post by Artim on 2019-08-03
Grrrrr, PPAs.  I always try to avoid them!

---

### Post by TheFu on 2019-08-03
I maintain fairly clean systems, avoiding any none core Canonical repos, never installing .deb files directly.
I can remember 1 major screw up with apt-get/apt in the last 10 years.  I had installed MariaDB instead of MySQL and some dependency decided that mysql was mandatory, so mariaDB was removed during an upgrade or dist-upgrade weekly patch.  That broke a project management system.  Since then, I think all Canonical packages recognize mariadb as equiv to mysql, so the problem hasn't reoccurred.  Sendmail, postfix, exim are all MTAs. Each fills the MTA dependency requirement, but very, very, very, few people would ever want more than 1 of them installed on the same machine.

I've never had any issues with either sudo apt autoclean or sudo apt autoremove - none. Zero. Nada. I don't know if I've just been lucky or others have been unlucky. 

I also have automatic, daily, versioned, backups, for all my systems.  If anything bad happened, restoring a system to almost the exact same as it was the day prior is 30-45 minutes of effort.  Restoring from 17 or 42 or 78 days ago isn't any harder.

If I want to try something new or different, I'll spin up a fresh VM and try it. That way, my normal servers and desktops aren't harmed.

---

### Post by cruzer001 on 2019-08-03
> **Artim said:**
> Grrrrr, PPAs.  I always try to avoid them!
Not all ppa's are bad.

Check their update history and current bug reports.  PPAs can be a reliable source and one that I would choose over flatpac or snaps.

---

### Post by boris12 on 2019-08-03
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic


```

---

### Post by boris12 on 2019-08-03
> **TheFu said:**
> I maintain fairly clean systems, avoiding any none core Canonical repos, never installing .deb files directly.
I can remember 1 major screw up with apt-get/apt in the last 10 years.  I had installed MariaDB instead of MySQL and some dependency decided that mysql was mandatory, so mariaDB was removed during an upgrade or dist-upgrade weekly patch.  That broke a project management system.  Since then, I think all Canonical packages recognize mariadb as equiv to mysql, so the problem hasn't reoccurred.  Sendmail, postfix, exim are all MTAs. Each fills the MTA dependency requirement, but very, very, very, few people would ever want more than 1 of them installed on the same machine.

I've never had any issues with either sudo apt autoclean or sudo apt autoremove - none. Zero. Nada. I don't know if I've just been lucky or others have been unlucky. 

I also have automatic, daily, versioned, backups, for all my systems.  If anything bad happened, restoring a system to almost the exact same as it was the day prior is 30-45 minutes of effort.  Restoring from 17 or 42 or 78 days ago isn't any harder.

If I want to try something new or different, I'll spin up a fresh VM and try it. That way, my normal servers and desktops aren't harmed.

That is a really nice approach ! Could you please post more info on how you backup your systems?

---

### Post by boris12 on 2019-08-03
> **cruzer001 said:**
> Not all ppa's are bad.

Check their update history and current bug reports.  PPAs can be a reliable source and one that I would choose over flatpac or snaps.

PPAs over snaps ? That is something I want to keep in mind ! Thought snaps are safer

---

### Post by Artim on 2019-08-03
At least PPAs - as long as the the PPA is maintained - install through APT and remain updated with regular updates.  I don't know if that's true of Snaps or Flatpacks yet.

---

