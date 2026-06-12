---
title: "'Package Dependencies cannot be resolved' When trying to install minitube-ubuntu"
date: 2014-09-05
forum: General Help
---

### Post by craig-fenton2 on 2014-09-05
When I try to install Minitube, the software centre stops and says: 
```
Package dependencies cannot be resolved 
This error could be caused by required additional software packages which are missing or not installable. 
Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time. 
Under the details section is the following text:
The following packages have unmet dependencies: 
minitube-ubuntu: Depends: libc6 (>= 2.14) but 2.19-0ubuntu6.3 is to be installed
Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed                  
Depends: libphonon4 (>= 4:4.2.0) but 4:4.7.1-0ubuntu8 is to be installed                  
Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed                  
Depends: libqt4-network (>= 4:4.5.3) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed                  
Depends: libqt4-script (>= 4:4.5.3) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed                  
Depends: libqt4-sql (>= 4:4.5.3) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed                  
Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed                  
Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed                  
Depends: libstdc++6 (>= 4.2.1) but 4.8.2-19ubuntu1 is to be installed                  
Depends: gstreamer0.10-ffmpeg but it is not going to be installed.
```

---

### Post by mc4man on 2014-09-05
> Depends: gstreamer0.10-ffmpeg but it is not going to be installed.
That package is no longer available in 14.04 & as usual the builds available via S-c are not updated properly.
(gstreamer0.10-ffmpeg for 14.04 is available [in my ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") but in this case don't know if it's really needed/useful

What you may wish is to get minitube from here, newer version, doesn't depend on gstreamer0.10-ffmpeg - 
[https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty)

---

