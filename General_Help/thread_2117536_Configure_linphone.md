---
title: "Configure linphone"
date: 2013-02-18
forum: General Help
---

### Post by habana on 2013-02-18
I am temporarily without a router, so no voip hardware at present. I thought I would try a softphone and downloaded linphone via synaptic. Looks simple enough but I cannot find any way of entering my VOIP provider's account settings. There are detailed instructions for mobile phone users but I am on a desktop. On the preferences>manage sip acount settings tab there is a "wizard" button that does nothing. There is a SIP account window but no way of adding a password etc.

Anybody got any bright ideas?

---

### Post by ZippyUbu on 2013-02-18
```
$ apt-cache show linphone
Package: linphone
Priority: optional
Section: universe/sound
Installed-Size: 232
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian VoIP Team <pkg-voip-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 3.3.2-4.1ubuntu1
Replaces: linphone-common (<< 3.1.2-2)
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libgdk-pixbuf2.0-0 (>= 2.22.0), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.31.2), libgtk2.0-0 (>= 2.16.0), liblinphone3 (>= 3.3.2), libmediastreamer0 (>= 3.3.2), libortp8 (>= 3.3.2), linphone-nox (= 3.3.2-4.1ubuntu1)
Suggests: yelp
Filename: pool/universe/l/linphone/linphone_3.3.2-4.1ubuntu1_amd64.deb
Size: 63168
MD5sum: 11dc0eff6fd65296520726e36145bfc7
SHA1: 265b00226e8405913d1977ae556c73f241fe6596
SHA256: 74347a4df643a5b356febc1054f2e7df6c4d1bc2c1eae0007a9cbb5df06c4018
Description-en: SIP softphone - graphical client
 Linphone is an audio and video internet phone using the SIP protocol. It
 has a GTK+ and console interface, includes a large variety of audio and video
 codecs, and provides IM features.
 .
 The main features of linphone are:
   - a nice graphical interface;
   - it includes a large variety of codecs with different quality / bandwidths;
   - it uses the well-known and standardised SIP protocol.
Homepage: http://www.linphone.org/
Description-md5: c8e338427d32f8210b697380bbeadba4
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu


```Hi - I think the  synaptic version is old. You could try a newer package direct from their website and see if it works...

Launchpad has a similar bug mentioned for previous versions - [https://bugs.launchpad.net/ubuntu/+source/linphone/+bug/566075](https://bugs.launchpad.net/ubuntu/+source/linphone/+bug/566075)

Try a newer version and hopefully all good...
[http://www.linphone.org/eng/download/packages/linphone.html](http://www.linphone.org/eng/download/packages/linphone.html)

--
Zu

---

### Post by habana on 2013-02-19
Thanks Zu. Actually the version I downloaded from synaptic is the latest version  - 3.5.2. Maybe I'll try another softphone!

---

