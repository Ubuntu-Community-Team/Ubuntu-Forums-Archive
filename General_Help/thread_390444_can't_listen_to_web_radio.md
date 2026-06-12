---
title: "can't listen to web radio"
date: 2007-03-21
forum: General Help
---

### Post by ddxperfecxion on 2007-03-21
just trying to listen to web radio but can't. i tried apt-get install w32codecs mplayer mozilla-mplayer but that didn't work.

---

### Post by DapperMe17 on 2007-03-22
Try Rhythymbox or Amarok.

Do a search in the Wiki for restricted codecs...there'll be a short list that you can copy from that page & paste to a terminal window. 

One of those add-ons is the key to streaming radio. Install them all & you're in business. Win32codecs is not enough for you.

---

### Post by ddxperfecxion on 2007-03-22
i used apt-get install for Rhythmbox and Amarok and i have the latest version. but i couldn't find the list you talked about.

---

### Post by fenian on 2007-03-22
Restricted format instuctions are [here]("https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29#head-f56c97ad320b887d84a64b9d69045f02dbdf28ba")
windows codec instructions are [here]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs") .

---

### Post by ddxperfecxion on 2007-03-22
still can't listen to it... this i what i got after putting the functions in for a 2nd time

```

apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

```

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
gstreamer0.10-pitfdll is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gxine is already the newest version.
libxine-main1 is already the newest version.
libxine-extracodecs is already the newest version.
ogle is already the newest version.
ogle-gui is already the newest version.
The following packages were automatically installed and are no longer required:
  dctc
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


```

everything looks good there


```

wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb

```

```

--08:25:28--  http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
           => `w32codecs_20061022-0.0_i386.deb'
Resolving www.debian-multimedia.org... 213.186.33.17
Connecting to www.debian-multimedia.org|213.186.33.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb [following]
--08:25:29--  http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
           => `w32codecs_20061022-0.0_i386.deb'
Resolving ftp.sunet.se... 194.71.11.69, 2001:6b0:19::64
Connecting to ftp.sunet.se|194.71.11.69|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.


```

not sure if this went right but then i did:

```

dpkg -i w32codecs_20061022-0.0_i386.deb

```

```

(Reading database ... 139575 files and directories currently installed.)
Preparing to replace w32codecs 1:20061022-0.0 (using w32codecs_20061022-0.0_i386.deb) ...
Unpacking replacement w32codecs ...
Setting up w32codecs (20061022-0.0) ...

```
that looks right too but i still can't listen to my show.

the site is 923freefm.com that may help to know what they are using.

---

### Post by fenian on 2007-03-22
If you are trying to listen to live radio from that site it appears that the liste live links on the page don't work,I get 404 errors from all of them.If you are trying to listen to previously recorded shows on that site you need to have sun java installed.Sun Java runtime can be installed from add/remove programs in the main menu.

---

