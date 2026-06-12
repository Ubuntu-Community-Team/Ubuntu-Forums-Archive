---
title: "Latest update (Feb.4, 2014) broke audio, video, unity"
date: 2014-02-04
forum: General Help
---

### Post by syrag on 2014-02-04
This update broke my system:

```
Start-Date: 2014-02-04  07:43:32
Commandline: aptdaemon role='role-commit-packages' sender=':1.77'
Upgrade: gnash-cygnal:amd64 (0.8.10-5ubuntu1, 0.8.10-5ubuntu1.1), 
fglrx:amd64 (8.960-0ubuntu1.1, 13.101-0ubuntu0.0.1), lightdm:amd64 (1.2.3-0ubuntu2.3, 1.2.3-0ubuntu2.4), 
python-apt:amd64 (0.8.3ubuntu7.1, 0.8.3ubuntu7.2), python-apt-common:amd64 (0.8.3ubuntu7.1, 0.8.3ubuntu7.2),
 konqueror-plugin-gnash:amd64 (0.8.10-5ubuntu1, 0.8.10-5ubuntu1.1), 
browser-plugin-gnash:amd64 (0.8.10-5ubuntu1, 0.8.10-5ubuntu1.1), gnash-common:amd64 (0.8.10-5ubuntu1, 0.8.10-5ubuntu1.1),
 dkms:amd64 (2.2.0.3-1ubuntu3.1, 2.2.0.3-1ubuntu3.2), google-chrome-stable:amd64 (32.0.1700.102-1, 32.0.1700.107-1), 
gnash:amd64 (0.8.10-5ubuntu1, 0.8.10-5ubuntu1.1), jockey-common:amd64 (0.9.7-0ubuntu7.11, 0.9.7-0ubuntu7.13),
 gnash-tools:amd64 (0.8.10-5ubuntu1, 0.8.10-5ubuntu1.1), jockey-kde:amd64 (0.9.7-0ubuntu7.11, 0.9.7-0ubuntu7.13), 
liblightdm-gobject-1-0:amd64 (1.2.3-0ubuntu2.3, 1.2.3-0ubuntu2.4), klash:amd64 (0.8.10-5ubuntu1, 0.8.10-5ubuntu1.1), 
fglrx-amdcccle:amd64 (8.960-0ubuntu1.1, 13.101-0ubuntu0.0.1), swfdec-gnome:amd64 (0.8.10-5ubuntu1, 0.8.10-5ubuntu1.1)
End-Date: 2014-02-04  08:00:14
```

I got a failed login: Failed to load session "ubuntu". I can load gnome or kde, but no unity 3d
I have no audio, and videos (whether flash in Firefox or Chrome or mov) play at ~5-10x normal speed. Mp4's appear normal speed, but without sound. 

I did installed ubuntu-desktop and got unity 2d, but I have no 3d, and no audio. I suspect the fglrx and/or lightdm updates are my problem.

Two questions: 1)does anyone else have a similar problem, and 2) how do I fix it?

Thanks

Edit: Also .dmrc settings, i.e., per user language settings are no longer recognized, and I can apparently no longer set lightdm as the default window manager.

---

### Post by syrag on 2014-02-04
It was the fglrx driver. I forced a downgrade from 13.101-0ubuntu to 8.960-0ubuntu and everything is working the way it always has.

---

### Post by Jason_Grimm on 2014-02-07
Technically this  is a workaround. There are some downsides to using the Ubuntu driver. One issue is an increase in artifacts in XBMC.

---

### Post by thctlo on 2014-02-19
Hai, If you use XBMC with the FGLRX ubuntu driver i can advice to use the 9.000 driver from quantal on ubuntu 12.04 with 3.2 kernel. 
Not 1 artifact. 

the 2:13.101-0ubuntu0.0.1 driver causes lots of artifacts, i got this "acidental" upgrade also. Just downgraded, and back to good again.

---

