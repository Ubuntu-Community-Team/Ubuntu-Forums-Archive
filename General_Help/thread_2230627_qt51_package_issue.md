---
title: "qt51 package issue?"
date: 2014-06-20
forum: General Help
---

### Post by lordbah2 on 2014-06-20
Running Ubuntu 13.10 and tried to update makerware from 3.0.1.50 to 3.2. Got lots of errors regarding QT 5.1.

Package qt51jsbackend failed to install/upgrade: parsing file '/var/lib/dpkg/tmp.ci/control' near line 12 package 'qt51jsbackend': duplicate value for 'Package' field.

Ditto for [FONT=Verdana]qt51base, [/FONT][FONT=Verdana]qt51xmlpatterns, qt51multimedia (qt51multimedia:amd64), qt51declarative, [/FONT][FONT=Verdana]qt51webkit.

Had a heck of a time cleaning up a broken package situation after this, but I think everything is wiped now.

/var/lib/dpkg/tmp.ci doesn't exist. I guess it must be something transient which exists during an install.

Is this a known issue? I didn't find it. Suggestions?

How can I tell whether these packages are coming from makerbot or qt-desktop.org or ubuntu.com or somewhere else? The package maintainer email address shown by synaptic is an unrouteable address according to gmail.[/FONT]

---

### Post by lordbah2 on 2014-06-22
lordbah@arctic:~$ apt-cache show qt51jsbackend
Package: qt51jsbackend
Version: 5.1.0-13.10
Architecture: amd64
Maintainer: Zoltán Balogh <zoltan@bakter.hu>
Installed-Size: 4997
Depends: libc6 (>= 2.14), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1)
Homepage: [http://www.qt-project.org](http://www.qt-project.org)
Priority: extra
Section: libs
Filename: pool/main/q/qt51jsbackend/qt51jsbackend_5.1.0-13.10_amd64.deb
Size: 1784484
SHA256: f6a1c46888267236535cced7d75d866830acf9bdcea011d4859eed11d6622949
SHA1: 801511750a738dfb739744f051467751403c8364
MD5sum: 801790b4257162a74fd0b1fe83e05112
Description: Qt V8 Javascript backend used by Qt Declarative.
 <insert long description, indented with spaces>
Description-md5: baebec95ba12fa4eef684bef4f22e317
Package: qt51jsbackend
Version: 5.1.0-13.10
Architecture: amd64
Maintainer: Zoltán Balogh <zoltan@bakter.hu>
Installed-Size: 4997
Depends: libc6 (>= 2.14), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1)
Homepage: [http://www.qt-project.org](http://www.qt-project.org)
Description: Qt V8 Javascript backend used by Qt Declarative.
 <insert long description, indented with spaces>

---

### Post by cmspooner on 2014-06-23
I'm in the same boat. I saw your post on the qt forums as well. Please update when you hear back from makebot.

---

### Post by lordbah2 on 2014-06-23
Haven't heard a peep from Makerbot. I was able to install by pointing to the raring repository, installing the qt51* packages, then pointing back to saucy to install makerware and libthing. But it still doesn't work. It knows the printer is there but it can't update firmware or set wifi settings or load filament or really do anything at all.

---

### Post by lordbah2 on 2014-06-25
Makerbot Support replied today - after a full week of silence - that there is a new version of software which has some fixes and I should install it. Sounds like update, cross your fingers, and hope the problems go away. I'll give it a try when I get home tonight, but I wanted to let you know now in case you want to try it now.

---

### Post by cmspooner on 2014-06-27
Still Fails...the problem seems to be qt51jsbackend

'qt51jsbackend':  duplicate value for `Package' field

---

