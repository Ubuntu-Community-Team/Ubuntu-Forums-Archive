---
title: "mpv not starting after install: liblua error"
date: 2018-02-09
forum: General Help
---

### Post by bric on 2018-02-09
I went here: [https://mpv.io/installation/](https://mpv.io/installation/)
and grabbed the repository [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)
installed mpv without errors or warnings but now when I try to use it.

> mpv: error while loading shared libraries: liblua5.2.so.0: cannot open shared object file: No such file or directory

I googled and tried
sudo apt-get install liblua5.2-0
sudo apt-get install liblua5.2-0:i386
to no effect.  Same error message.

Help?

---

### Post by #&amp;thj^% on 2018-02-09
What version of Ubuntu are you using? And Desktop environment?
If this is on a wayland session logout and login under X11/Xorg
Depends On:
```
ffmpeg  lcms2  libcdio-paranoia  libgl  libxss  libxinerama
                  libxv  libxkbcommon  libva  wayland  libcaca
                  desktop-file-utils  hicolor-icon-theme  xdg-utils  lua52
                  libdvdnav  libxrandr  jack  rubberband  uchardet  libarchive
                  smbclient
``` 
Just some thoughts to check.

---

### Post by mc4man on 2018-02-09
In addition to the above info also add
```
locate liblua5
```
and 
```
ldd /usr/bin/mpv |grep lua
```

---

### Post by bric on 2018-02-10
It's Ubuntu 17.10 ... Desktop version ... so apparently 'wayland session' (wasn't even aware of that)

locate liblua5 yields:
> /usr/lib/x86_64-linux-gnu/liblua5.3-c++.so.0
/usr/lib/x86_64-linux-gnu/liblua5.3-c++.so.0.0.0
/usr/lib/x86_64-linux-gnu/liblua5.3.so.0
/usr/lib/x86_64-linux-gnu/liblua5.3.so.0.0.0
/usr/share/doc/liblua5.2-0
/usr/share/doc/liblua5.3-0
/usr/share/doc/liblua5.2-0/changelog.Debian.gz
/usr/share/doc/liblua5.2-0/copyright
/usr/share/doc/liblua5.3-0/changelog.Debian.gz
/usr/share/doc/liblua5.3-0/copyright
/var/lib/dpkg/info/liblua5.2-0:amd64.list
/var/lib/dpkg/info/liblua5.2-0:amd64.md5sums
/var/lib/dpkg/info/liblua5.2-0:amd64.shlibs
/var/lib/dpkg/info/liblua5.2-0:amd64.triggers
/var/lib/dpkg/info/liblua5.3-0:amd64.list
/var/lib/dpkg/info/liblua5.3-0:amd64.md5sums
/var/lib/dpkg/info/liblua5.3-0:amd64.shlibs
/var/lib/dpkg/info/liblua5.3-0:amd64.triggers


ldd /usr/bin/mpv | grep lua gives:
> liblua5.2.so.0 => not found

I will go and attempt to figure out how to boot using X11 now... and report back...

Medium-success! (I'm logged in with X11)
and now the mpv command yields...

mpv: error while loading shared libraries: liblua5.2.so.0: cannot open shared object file: No such file or directory

and the other commands look the same as above.

> **1fallen said:**
> Depends On:
```
ffmpeg  lcms2  libcdio-paranoia  libgl  libxss  libxinerama
                  libxv  libxkbcommon  libva  wayland  libcaca
                  desktop-file-utils  hicolor-icon-theme  xdg-utils  lua52
                  libdvdnav  libxrandr  jack  rubberband  uchardet  libarchive
                  smbclient
``` 

Did this mean that these are dependencies required by mpv and that I should check that they are installed? And is there a particular way I should do that (apart from running apt-get install ...)?

---

### Post by mc4man on 2018-02-10
Please post 
```
apt-cache policy mpv liblua5.2
```
```
which mpv
```
There is no way the ppa mpv package would install without installing liblua5.2 nor could the liblua5.2 package be removed without removing that mpv package.
Ex.
> sudo apt install mpv
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  i965-va-driver libaacs0 libbdplus0 libbluray2 libbs2b0 libdvdnav4 libdvdread4 libfdk-aac1 libgme0 libgsm1 [COLOR="#0000CD"]liblua5.2-0[/COLOR]
  libmodplug1 libmp3lame0 libmysofa librubberband2v5 libsoxr0 libtwolame0 libuchardet0 libva-drm1 libva-wayland1 libva-x11-1
  libva1 libvdpau1 libxvidcore4 mesa-va-drivers mesa-vdpau-drivers va-driver-all vdpau-driver-all


```
sudo apt purge liblua5.2
......
The following packages will be REMOVED:
  liblua5.2-0* mpv*
0 upgraded, 0 newly installed, 2 to remove ..
```

---

### Post by #&amp;thj^% on 2018-02-10
> **mc4man said:**
> 
There is no way the ppa mpv package would install without installing liblua5.2 nor could the liblua5.2 package be removed without removing that mpv package.

+1>>>That was my thoughts also.
now very curious how OP installed and version of MPV?!

---

### Post by bric on 2018-02-10
```
$ apt-cache policy mpv liblua5.2
mpv:
  Installed: 2:0.27.0+git2~zzartful
  Candidate: 2:0.27.0+git2~zzartful
  Version table:
 *** 2:0.27.0+git2~zzartful 500
        500 [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu) artful/main amd64 Packages
        100 /var/lib/dpkg/status
     0.26.0-3ubuntu1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) artful/universe amd64 Packages
liblua5.2-0-dbg:
  Installed: (none)
  Candidate: 5.2.4-1.1build1
  Version table:
     5.2.4-1.1build1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) artful/main amd64 Packages
liblua5.2-dev:
  Installed: (none)
  Candidate: 5.2.4-1.1build1
  Version table:
     5.2.4-1.1build1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) artful/main amd64 Packages
liblua5.2-0:
  Installed: 5.2.4-1.1build1
  Candidate: 5.2.4-1.1build1
  Version table:
 *** 5.2.4-1.1build1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) artful/main amd64 Packages
        100 /var/lib/dpkg/status
```

and

```
$ which mpv
/usr/bin/mpv

```

As to how I originally installed... I wish I could tell you. I've had mpv running in the past but I think on 14.04 or something and I've done clean installs every year or two.

This has come up because I was playing with 'Emby' and probably (?) followed [these instructions]("https://emby.media/community/index.php?/topic/42868-emby-theater-for-linux/?p=399462"), at least originally.  When mpv didn't work who knows what I tried.  The first time I played with that was months ago and now that I look at it again...well, my memory's not that good.  Sorry.

I might have had liblua5.2 installed already as part of Apache2.


SOLUTION:

Thanks for the help.  The [comment about how mpv could not install/uninstall without liblua5.2]("https://ubuntuforums.org/showthread.php?t=2384638&p=13738673#post13738673")  inspired me to start over.  
I purged mpv and when I didn't see liblua listed in the files to be removed, I looked to see what removing it seperately would do (hence my observation about Apache).  Then I did a quick backup of some of the config I've done with that.
Then did purge of liblua5.2-0 (which removed Apache).
Updated.
Then re-installed Apache.
Then re-installed mpv (definitely coming from the repo this time).

And now it works.
Hopefully, I haven't buggered any of my other software by fiddling with Apache like that. I suppose I'll find out.

Thanks very much.  You did give me the clue I needed.

---

