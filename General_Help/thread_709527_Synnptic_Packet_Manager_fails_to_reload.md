---
title: "Synnptic Packet Manager fails to reload"
date: 2008-02-27
forum: General Help
---

### Post by xtrumanx on 2008-02-27
HELP! I'm trying to reload Synpatic Packet Manager after turning on some repositories and it won't reload. Also, apt-get update doesn't want to do its thing. I'm not sure if this has always been like this, but while its attempting to connect, the following text can be seen in the terminal:
[Connecting to archive.ubuntu.com (1.0.0.0)]

That 1.0.0.0 doesn't look right. Oddly enough, if I ping archive.ubuntu.com (showing the correct IP address) then follow up with apt-get update, the apt-get update goes through normally.

I don't think I've screwed anything up (not intentionally at least). I just disabled ipv6 on firefox (otherwise, firefox itself won't work) and turned on the universe and multiverse repositories and installed vlc (with some luck). Other than that, I'm using a fresh Ubuntu 7.10 install. Thanks in advance.

P.S. I am no expert, but is there a way to disable ipv6 system wide? Disabling it seems to make firefox work fine, but now I'm wondering if the same solution would work for apt-get and synpatic.

---

### Post by SunnyRabbiera on 2008-02-27
are you getting errors using apt get?

---

### Post by xtrumanx on 2008-02-27
Below is what happen when I apt-get update:

```
~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err http://archive.ubuntu.com gutsy Release.gpg           
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com gutsy/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com gutsy/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com gutsy/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Also while attempting to connect, this is what is showing:

```
54% [Connecting to archive.ubuntu.com (1.0.0.0)]
```

---

