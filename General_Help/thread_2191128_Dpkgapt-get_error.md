---
title: "Dpkg/apt-get error"
date: 2013-12-01
forum: General Help
---

### Post by jono-cooper on 2013-12-01
Hi,

Long time reader first time poster. I've scoured Google and these forums for this but I'm at a loss, I'm having two issues. One being my RAID/LVM array has done a disappearing act (spotted a UUID issue here) and another being an update issue with dpkg. I'm unsure if they're related, however I want to fix one at a time, starting with the dpkg one.

So, here's the error:
```

root@localhost:/home/exodus-server# apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils libapt-inst1.4 libapt-pkg4.12 pm-utils
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,409 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 85%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'gstreamer0.10-plugins-good' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Here's a couple of things I've tried and their respective results:
```

root@localhost:~# apt-get remove --purge gstreamer0.10-plugins-good
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  empathy* gnome-media* gstreamer0.10-plugins-good* libfarstream-0.1-0* libpurple0* libtelepathy-farstream2* rhythmbox* rhythmbox-mozilla*
  rhythmbox-plugin-cdrecorder* rhythmbox-plugin-magnatune* rhythmbox-plugin-zeitgeist* rhythmbox-plugins* rhythmbox-ubuntuone* telepathy-haze* totem*
  totem-mozilla* totem-plugins* ubuntu-desktop* unity-scope-musicstores*
0 upgraded, 0 newly installed, 19 to remove and 6 not upgraded.
After this operation, 24.6 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 85%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'gstreamer0.10-plugins-good' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

```

root@localhost:~# dpkg --configure -a
root@localhost:~# apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils libapt-inst1.4 libapt-pkg4.12 pm-utils
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,409 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 85%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'gstreamer0.10-plugins-good' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

```

root@localhost:~# ls -l /var/lib/dpkg/info/*gstreamer0.10-plugins-good*
-rw-r--r-- 1 root root 5194 Sep 23 18:30 /var/lib/dpkg/info/gstreamer0.10-plugins-good:amd64.list
-rw-r--r-- 1 root root 7641 Feb 27  2013 /var/lib/dpkg/info/gstreamer0.10-plugins-good:amd64.md5sums
-rwxr-xr-x 1 root root  135 Feb 27  2013 /var/lib/dpkg/info/gstreamer0.10-plugins-good:amd64.postinst
-rwxr-xr-x 1 root root  132 Feb 27  2013 /var/lib/dpkg/info/gstreamer0.10-plugins-good:amd64.postrm
-rw-r--r-- 1 root root  109 Feb 27  2013 /var/lib/dpkg/info/gstreamer0.10-plugins-good:amd64.shlibs

```

```

Grep of STATUS Result:

Package: gstreamer0.10-plugins-good
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 5164
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: amd64
Source: gst-plugins-good0.10
Version: 0.10.31-1ubuntu1.2
Replaces: gstreamer0.10-plugins-bad (<< 0.10.21.2), gstreamer0.10-plugins-good-doc (<< 0.10.6-2), gstreamer0.10-plugins-really-bad (<< 0.10.21.2)
Provides: gstreamer0.10-audiosink, gstreamer0.10-audiosource, gstreamer0.10-videosink, gstreamer0.10-videosource, gstreamer0.10-visualization
Depends: libaa1 (>= 1.4p5), libavc1394-0 (>= 0.5.3), libbz2-1.0, libc6 (>= 2.14), libcaca0 (>= 0.99.beta17-1), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdv4, libflac8 (>= 1.2.1), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.31.8), libgstreamer-plugins-base0.10-0 (>= 0.10.36), libgstreamer0.10-0 (>= 0.10.36), libgudev-1.0-0 (>= 147), libiec61883-0 (>= 1.2.0), libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116, libjpeg8 (>= 8c), liborc-0.4-0 (>= 1:0.4.16), libpng12-0 (>= 1.2.13-4), libraw1394-11, libshout3, libsoup-gnome2.4-1 (>= 2.27.4), libsoup2.4-1 (>= 2.26.1), libspeex1 (>= 1.2~beta3-1), libstdc++6 (>= 4.1.1), libtag1c2a (>= 1.5), libv4l-0 (>= 0.5.0), libwavpack1 (>= 4.40.0), libx11-6, libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxml2 (>= 2.7.4), libxv1, zlib1g (>= 1:1.1.4), gstreamer0.10-plugins-base
Pre-Depends: multiarch-support
Recommends: gstreamer0.10-x
Breaks: gstreamer0.10-plugins-bad (<< 0.10.21.2), gstreamer0.10-plugins-really-bad (<< 0.10.21.2)
Description: GStreamer plugins from the "good" set
 GStreamer is a streaming media framework, based on graphs of filters
 which operate on media data.  Applications using this library can do
 anything from real-time sound processing to playing videos, and just
 about anything else media-related.  Its plugin-based architecture means
root@localhost:~# 

```

```

root@localhost:~# ls -l /var/lib/dpkg/status*
-rw-r--r-- 1 root root 1678439 Dec  1 19:53 /var/lib/dpkg/status
-rw-r--r-- 1 root root 1678439 Dec  1 14:30 /var/lib/dpkg/status.bk
-rw-r--r-- 1 root root 1678439 Dec  1 19:53 /var/lib/dpkg/status-old

```

Here's what I'm running (64Bit):
```

root@localhost:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"

```

I hopefully haven't drowned this in information. I've done my fair share of reading and I think this was more or less the basics of what I needed to cover. 

I would love any help on where to start looking to repair this!

Cheers,

Jon

---

### Post by jono-cooper on 2013-12-01
Ok, while there hasn't been any responses there is a solution. Although it's not great. I'll pop it here in case anyone else stumbles across this.

Basically this error was linked to my disappearing RAID/LVM. What I failed to mention in my last post was that when I SSH'd in to my box there was banner flagging an error and inability to execute a binary, namely 'lesspipe'.

A review of lesspipe in a hex editor showed that it was zeroed out. That is, full of zeroes. Subsequently it appeared that a fairly major system corruption had occurred. I gave a friend access to my box and he confirmed the same, something has occurred during the update process which has caused a fairly extensive system corruption - the giveaway was in the SSH banner and the contents of the failed binary.

That issue was subsequently causing the nodes to be altered/incorrectly referenced in relation to the LVM.

The solution - fresh install. I'm in the process of doing that now, thankfully the 6.0TB RAID5 LVM survived intact and should be able to be imported into the fresh install. Oddly enough 'fsck' showed that the drive hosting the OS was fine, so don't be fooled by that, this was at the software level, post boot.

As I said, it's not great but the issue was all-but unrecoverable. It's a solution, not the greatest one but it is an answer. Hopefully this helps someone else.

---

