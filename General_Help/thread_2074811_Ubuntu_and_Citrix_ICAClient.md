---
title: "Ubuntu and Citrix ICAClient"
date: 2012-10-22
forum: General Help
---

### Post by thomi_ch on 2012-10-22
Heyy all

I create this thread cause there is a very old one, that maybe isn't read by everyone ;):
[http://ubuntuforums.org/showthread.php?t=891022](http://ubuntuforums.org/showthread.php?t=891022)

Installing Citrix icaclient on ubuntu, specially 64bit, isn't easy...

Upgraded yesterday from 12.04 to 12.10 and icaclient (12.0) won't work

/opt/Citrix/ICAClient/wfica -desc "TEST"
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(wfica:19103): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed
Segmentation fault (core dumped)

I tried then to install latest icaclient v12.1 amd64 and needed to get a patched version, check this:
[http://askubuntu.com/questions/14715...kage-icaclient](http://askubuntu.com/questions/14715...kage-icaclient)

Installation of icaclient was success, but still same arrer (see above).

Here some information:

apt-cache policy icaclient
icaclient:
Installed: 12.1.0
Candidate: 12.1.0
Version table:
*** 12.1.0 0
100 /var/lib/dpkg/status


apt-cache policy libmotif4
libmotif4:
Installed: 2.3.3-5ubuntu2
Candidate: 2.3.3-5ubuntu2
Version table:
*** 2.3.3-5ubuntu2 0
500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) quantal/multiverse amd64 Packages
100 /var/lib/dpkg/status


apt-cache policy libjpeg8
libjpeg8:
  Installed: 8c-2ubuntu7
  Candidate: 8c-2ubuntu7
  Version table:
 *** 8c-2ubuntu7 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status


I tried some stuff from [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo) but without success.

Maybe some of you can help, give a hint.

Thanks a lot

Cheers
thomi

---

### Post by thomi_ch on 2012-10-29
Information about installation problem on [K]ubuntu 12.10 and ICAClient 12.1 amd64 you can find here:
[Ask Ubuntu: Citrix Receiver on Ubuntu 12.10?]("http://askubuntu.com/questions/204312/citrix-receiver-on-ubuntu-12-10")

thomi

---

### Post by father_ted on 2012-12-28
Im having a try at getting this to work on x64 as it would be nice for work. Its getting stuck looking for **lib32asound2** - which i think is an older deprecated package. Im going to trawl forums awhile and see if i can find any workarounds - which i will post here. Im hoping someone else will have encountered this and worked around it.

---

