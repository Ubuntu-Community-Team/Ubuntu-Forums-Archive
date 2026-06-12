---
title: "problem with muse in ubuntu 15.10"
date: 2016-04-16
forum: General Help
---

### Post by rwkaye on 2016-04-16
dear forum,

there's a problem with the version of muse shipped with ubuntu 15.10

$ muse
muse: error while loading shared libraries: libmuse_core.so: cannot open shared object file: No such file or directory

$ lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

the file is installed:

$ find /usr -name "*libmuse*"
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_arranger.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_core.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_awl.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_cliplist.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_master.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_synti.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_midiedit.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_icons.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_widgets_functiondialogs.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_widgets.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_driver.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_al.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_mixer.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_waveedit.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_mplugins.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_liste.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_marker.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_instruments.so
/usr/lib/x86_64-linux-gnu/muse/modules/libmuse_ctrl.so

any suggestions as to what I am supposed to do?

thanks
Richard

---

### Post by gordintoronto on 2016-04-16
Did you find this page:
[https://linuxmusicians.com/viewtopic.php?t=14618](https://linuxmusicians.com/viewtopic.php?t=14618)

---

### Post by rwkaye on 2016-04-17
> **gordintoronto said:**
> Did you find this page:
[https://linuxmusicians.com/viewtopic.php?t=14618](https://linuxmusicians.com/viewtopic.php?t=14618)

Yes I did.  However the "temporary solution" there does not work for ubuntu 15.10.  Installing the deb file there produces a lot of dependency problems.  It seems like this "temporary solution" needs libraries/packages such as libcairomm-1.0-1 whereas Ubuntu 15.10 provides libcairomm-1.0-1v5 .  There are about half a dozen other such dependencies I cannot resolve on my ubuntu.

---

### Post by rwkaye on 2016-04-17
OK I see what to do now!

Follow the instructions at 

[http://kxstudio.linuxaudio.org/Repositories](http://kxstudio.linuxaudio.org/Repositories)

to install various debs that activate the kxstudio repositories

Then update package information (I used synaptic, edit -> reload package information) and upgrade muse and other packages.

All works now.

I presume these changes will eventually make their way to the Ubuntu distro?  Clearly these debs supplied with 15.10 are broken.

Richard

---

