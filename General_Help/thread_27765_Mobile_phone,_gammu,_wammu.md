---
title: "Mobile phone, gammu, wammu"
date: 2005-04-17
forum: General Help
---

### Post by hamil on 2005-04-17
Hello!

I have been searching the net for some good software for my mobile phones.
I found a project called gammu, with the GUI called wammu.
I tried to install it on my old 4.10, without any success, so I just forgot about it for a while.
After I upgraded to 5.04, I figured I wanted to give it a try again... Since I wanted to backup my mobile etc.

* I first installed gammu-1.01.0 with shared libraries, no problem
* Next step is installing python-gammu, there I bump into some trouble...
I run the command: python setup.py build, and get the following error messages:
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)

But, I do have Python 2.4 installed. The directory /usr/lib/python2.4 does exist, but the subdirectory called /config/ is not there....
Anyone have any clue how I am supposed to get further?

Looking forward to get some help here... :)

Brgds
/Lasse

---

### Post by GOwin on 2005-07-03
I'm also trying to use python-gammu. [www.cihar.com](www.cihar.com) host deb packages but I can't install python-gammu.

I'm using python v2.4.1 and the maintainer told me to "Just rebuild it against python you use, debian/rules currently do not support build for multiple python versions."

Michal had been helpful and told me that I can "Download tarball, unpack it and use dpkg-buildpackage."

I'm still quite new to linux and I had trouble using dpkg-buildpackage. It seems that it's still trying to look for python2.3.

Could someone please tell me what I'm supposed to do?

Thanks

---

