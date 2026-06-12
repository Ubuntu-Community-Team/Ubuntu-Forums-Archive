---
title: "Xubuntu 16.04 proposed repos enabled but not by me."
date: 2016-12-16
forum: General Help
---

### Post by ajgreeny on 2016-12-16
I have just noticed that the proposed repos were enabled in my Xubuntu 16.04 system, but I do not remember enabling them, and more importantly, I could not disable them from software-sources in the usual way.

The entry for using proposed was eventually found in **/etc/apt/sources.list.d** and was not a line in the sources.list file itself.
I removed the two files (proposed.list and proposed.list.save) as that was the only way to disable proposed, and I now find that enabling and disabling proposed in software-sources as usual is possible and when enabled it adds a proposed line as expected to the bottom of /etc/apt/sources.list.

I managed to find a launchpad bug for this at [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1592427](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1592427) to which I have added  my comments, but I am wondering if anyone has a clue what is going on.

I've now disabled proposed and hope that the packages that I have unknowingly installed from proposed in the past do not cause big problems in future. All runs well at present to I am hopeful, but I do wonder how and why it happened in the first place.

---

### Post by #&amp;thj^% on 2016-12-16
ajgreeny I don't have an answer as to why  proposed repos were enabled by default.
But as a reassurence "hopefully" I have had proposed on since it was in devolvement with nothing bad or even noticeable with my system.
There is a long painful way to find what has been upgraded or installed by proposed with synaptic using the Origin slot on the left side and scrolling to the respective areas IE:
```
xenial-proposed-main
xenial-proposed-security
xenial-proposed/multiverse 
xenial-proposed/restricted
```
and clicking each one...should now show you what has been upgraded from there.
Just an example from mine:
```
apt policy gstreamer1.0
gstreamer1.0-plugins-ugly-amr:
  Installed: 1.8.3-1ubuntu0.1
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
 *** 1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-videosink:
  Installed: (none)
  Candidate: (none)
  Version table:
gstreamer1.0-alsa:
  Installed: 1.8.3-1ubuntu0.1
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
 *** 1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-plugins-ugly-dbg:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
     1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
     1.8.2-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-plugins-ugly-doc:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
     1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe i386 Packages
     1.8.2-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
     1.8.1-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
gstreamer1.0-plugins-base-apps:
  Installed: 1.8.3-1ubuntu0.1
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
 *** 1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
libgstreamer1.0-dev:
  Installed: (none)
  Candidate: 1.8.3-1~ubuntu0.1
  Version table:
     1.8.3-1~ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
     1.8.2-1~ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     1.8.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-hybris:i386:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
     1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe i386 Packages
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
gstreamer1.0-tools:
  Installed: 1.8.3-1~ubuntu0.1
  Candidate: 1.8.3-1~ubuntu0.1
  Version table:
 *** 1.8.3-1~ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1~ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     1.8.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-plugins-good:
  Installed: 1.8.3-1ubuntu0.2
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
 *** 1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-qapt:
  Installed: (none)
  Candidate: (none)
  Version table:
libgstreamer1.0-0-dbg:
  Installed: (none)
  Candidate: 1.8.3-1~ubuntu0.1
  Version table:
     1.8.3-1~ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
     1.8.2-1~ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     1.8.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-espeak:
  Installed: (none)
  Candidate: 0.4.0-1
  Version table:
     0.4.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-nice:
  Installed: (none)
  Candidate: 0.1.13-0ubuntu2
  Version table:
     0.1.13-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-videosource:
  Installed: (none)
  Candidate: (none)
  Version table:
gstreamer1.0-crystalhd:
  Installed: (none)
  Candidate: 1:0.0~git20110715.fdd2f19-11build1
  Version table:
     1:0.0~git20110715.fdd2f19-11build1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-fluendo-mp3:
  Installed: 0.10.32.debian-1
  Candidate: 0.10.32.debian-1
  Version table:
 *** 0.10.32.debian-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
gstreamer1.0-plugins-bad:
  Installed: 1.8.3-1ubuntu0.2
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
 *** 1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-plugins-base:
  Installed: 1.8.3-1ubuntu0.1
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
 *** 1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-audiosource:
  Installed: (none)
  Candidate: (none)
  Version table:
gstreamer1.0-plugins-bad-videoparsers:
  Installed: 1.8.3-1ubuntu0.2
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
 *** 1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-plugins-really-bad:
  Installed: (none)
  Candidate: (none)
  Version table:
gstreamer1.0-clutter:
  Installed: (none)
  Candidate: 2.0.18-1
  Version table:
     2.0.18-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-pulseaudio:
  Installed: 1.8.3-1ubuntu0.2
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
 *** 1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-pocketsphinx:
  Installed: (none)
  Candidate: 0.8.0+real5prealpha-1ubuntu2
  Version table:
     0.8.0+real5prealpha-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-plugins-bad-dbg:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
     1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-plugins-bad-doc:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
     1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe i386 Packages
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
gstreamer1.0-visualization:
  Installed: (none)
  Candidate: (none)
  Version table:
gstreamer1.0-plugins-bad-faad:
  Installed: 1.8.3-1ubuntu0.2
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
 *** 1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-lame:
  Installed: (none)
  Candidate: (none)
  Version table:
gstreamer1.0-x:
  Installed: 1.8.3-1ubuntu0.1
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
 *** 1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-vaapi-doc:
  Installed: (none)
  Candidate: 1.8.3-1~ubuntu0.1
  Version table:
     1.8.3-1~ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe i386 Packages
     1.8.2-1~ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
     1.8.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
gstreamer1.0-libav:
  Installed: 1.8.3-1ubuntu0.1
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
 *** 1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1~ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     1.8.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-plugins-base-dbg:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
     1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-plugins-good-dbg:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
     1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
     1.8.2-1ubuntu0.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-plugins-base-doc:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
     1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main i386 Packages
     1.8.2-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
gstreamer1.0-plugins-good-doc:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.2
  Version table:
     1.8.3-1ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main i386 Packages
     1.8.2-1ubuntu0.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
gstreamer1.0-dvswitch:
  Installed: (none)
  Candidate: 0.1.1-1
  Version table:
     0.1.1-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-clutter-3.0:
  Installed: 3.0.18-1
  Candidate: 3.0.18-1
  Version table:
 *** 3.0.18-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
gstreamer1.0-vaapi:
  Installed: (none)
  Candidate: 1.8.3-1~ubuntu0.1
  Version table:
     1.8.3-1~ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
     1.8.2-1~ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     1.8.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-libav-dbg:
  Installed: (none)
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
     1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
     1.8.2-1~ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     1.8.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-packagekit:
  Installed: (none)
  Candidate: 0.8.17-4ubuntu6~gcc5.4ubuntu1.1
  Version table:
     0.8.17-4ubuntu6~gcc5.4ubuntu1.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     0.8.17-4ubuntu6~gcc5.4ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
libgstreamer1.0-0:
  Installed: 1.8.3-1~ubuntu0.1
  Candidate: 1.8.3-1~ubuntu0.1
  Version table:
 *** 1.8.3-1~ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1~ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     1.8.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
gstreamer1.0-ffmpeg:
  Installed: (none)
  Candidate: (none)
  Version table:
gstreamer1.0-plugins-ugly:
  Installed: 1.8.3-1ubuntu0.1
  Candidate: 1.8.3-1ubuntu0.1
  Version table:
 *** 1.8.3-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.8.2-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     1.8.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gstreamer1.0-doc:
  Installed: (none)
  Candidate: 1.8.3-1~ubuntu0.1
  Version table:
     1.8.3-1~ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main i386 Packages
     1.8.2-1~ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
     1.8.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
gstreamer1.0-audiosink:
  Installed: (none)
  Candidate: (none)
  Version table:
me@me-System-Product-Name:~$ 

```
I would be more worried now that it was disabled and potential breakage down the road with just regular (Stable) updates.
There is a way (again long and painful) to revert back to stable-updates:
found here:[http://askubuntu.com/questions/768849/how-to-reverse-proposed-channel-package-upgrade](http://askubuntu.com/questions/768849/how-to-reverse-proposed-channel-package-upgrade)
Just trying to be helpful.
Kind Regards

---

### Post by DuckHook on 2016-12-16
Hi ajgreeny

Have you installed anything recently via script? Some will frustratingly add their own entries to */etc/apt/sources.list.d* and not */etc/apt/sources.list* as one would expect from a well-behaved app. This happened to me with *google-chrome*. I had to move the line into the file I wanted and delete it from the *sources.list.d* directory.

---

### Post by ajgreeny on 2016-12-16
Thanks both.

@1fallen
I use synaptic generally when not using terminal so I am already aware of the Origin trick to see what has come from the proposed repos, and it looks as if there are quite a few packages from them which have been upgraded including all the gstreamer (and libgstreamer) packages you show.
Thanks also for the info about possible downgrading to stable versions; if I run into any problems in future I may give that a try as it actually looks quite straightforward to do, but I'm willing to take a chance for now and see where it takes me.

@DuckHook
No, nothing installed that way, though I have added a few ppa repos for things as I have always done, but I am not aware of why any of those would have added the proposed repos in the /etc/apt/sources.list.d/ folder as happened.
Just as a trial I have restored the proposed.list file to /etc/apt/sources.list.d/ which is where I found it and once again I am not able to disable the proposed repos from software-sources GUI.
Removing that proposed.list file again as I did before has once more disabled the proposed repos.

So it looks as if something has added those proposed.list files to /etc/apt/sources.list.d/ with no reference to me, and I am completely baffled about what has been done, by what, and why it happened.

---

### Post by DuckHook on 2016-12-16
> **ajgreeny said:**
> …I am completely baffled about what has been done, by what, and why it happened.…well, you do know that that dude in the avatar you've chosen ***is*** a pretty mischievous character… :?:

…just sayin'

---

### Post by #&amp;thj^% on 2016-12-16
> **DuckHook said:**
> …well, you do know that that dude in the avatar you've chosen ***is*** a pretty mischievous character… :?:

…just sayin'
Ah Ha...you could be on to something there DH ;)

---

### Post by ajgreeny on 2016-12-16
Oh heck, I hadn't thought about that!

I have added all my findings as shown in this thread to the launchpad bug linked above, and it seems to have started a new rush of interest, so we'll see if it gets anywhere.

I am still very baffled as to why the proposed.list  file was added to /etc/apt/sources.list.d and not simply as a repo line in /etc/apt/sources.list.

EDIT:
In spite of my comment earlier and having then read a bit more about the sense of downgrading from the proposed repos, I did use the suggestion 1fallen showed.
All downgraded to the stable repos as it was supposed to, and I am now posting this from a reboot after doing everything suggested.

All is good now and as it should be, so many thanks for that find, 1fallen.

---

### Post by ajgreeny on 2017-02-11
Just a quick, and now very late update to this thread.

I have just realised that the cause of this problem is that I installed the Xubuntu OS which had this problem by using an iso image that I downloaded from the daily-CD site at [http://cdimage.ubuntu.com/xubuntu/xenial/daily-live/pending/xenial-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/xubuntu/xenial/daily-live/pending/xenial-desktop-amd64.iso.zsync), updating the older ISO image that I had already downloaded a long time ago to run in VBox as a trial.

It did not occur to me that the pending daily-CD might have proposed repos enabled by default, but it certainly does, now confirmed by my installation two days ago of Lubuntu from an iso file once again updated with zsync from the daily-CD site.

You live and learn!

---

