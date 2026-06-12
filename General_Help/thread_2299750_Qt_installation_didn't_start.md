---
title: "Qt installation didn't start"
date: 2015-10-21
forum: General Help
---

### Post by its_bigB on 2015-10-21
Hi all,

I've download the Qt as per the following instructions ([https://wiki.qt.io/Install_Qt_5_on_Ubuntu](https://wiki.qt.io/Install_Qt_5_on_Ubuntu)) and try to install. But the command fail with the following error message.

> bash: ./qt-linux-opensource-5.0.2-x86-offline.run: No such file or directory

However, the offline file was there is the root, confirmed with ls -ltr. I've no idea what it really says file not found.

Thanks in advance.

---

### Post by Bucky Ball on 2015-10-21
The link you provided gives instructions for installing qt5 on 12.10, an old, unsupported release. Both the link and the release are obsolete.

Try [this]("http://www.bogotobogo.com/Qt/Qt5_Install_Ubuntu_14_64bit.php"). Check out the Software Centre also. I have qt5-default in there along with a bunch of other qt5 stuff so you can possibly get it straight from there.

If you are still using 12.10, suggest you upgrade to a supported release rather than persist with it. Good luck.

---

### Post by its_bigB on 2015-10-21
Thanks.

I'm using 14.04 and I thought this will work, I'll try to find the relevant update then. Is there a generic way to download these software in Ubuntu?

---

### Post by its_bigB on 2015-10-21
> **Bucky Ball said:**
> The link you provided gives instructions for installing qt5 on 12.10, an old, unsupported release. Both the link and the release are obsolete.

Try [this]("http://www.bogotobogo.com/Qt/Qt5_Install_Ubuntu_14_64bit.php"). Check out the Software Centre also. I have qt5-default in there along with a bunch of other qt5 stuff so you can possibly get it straight from there.

If you are still using 12.10, suggest you upgrade to a supported release rather than persist with it. Good luck.

I've one question, that I'm unable to find it in Qt downloads.

On the download page I can see only a package for Linux. Nothing specifically for Ubuntu. Will it work? In the details page it didn't mention anything about the different OSs.

---

### Post by Bucky Ball on 2015-10-21
Yes, should do. If you are talking about the one linked to on the link I suggested [here]("http://www.bogotobogo.com/Qt/Qt5_Install_Ubuntu_14_64bit.php").

---

