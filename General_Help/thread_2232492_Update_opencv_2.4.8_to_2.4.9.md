---
title: "Update opencv 2.4.8 to 2.4.9"
date: 2014-07-02
forum: General Help
---

### Post by MickSulley on 2014-07-02
I have opencv 2.4.8 installed.  I want to install the latest version of DigiKam which has opencv 2.4.9 as a pre-requisite, but this is not in the repositories

I have downloaded opencv-2.4.9.zip but the info in the readme does not tell me how to install it.  I currently have 43 packages that look like they belong to opencv, do I need to remove them first?  How do I install?

Thanks
Mick

---

### Post by bapoumba on 2014-07-03
Where are you getting digikam and where did you get opencv from ?

---

### Post by MickSulley on 2014-07-03
I got Digikam with
git clone git://anongit.kde.org/digikam-software-compilation

and opencv downloaded from 
[http://opencv.org/downloads.html](http://opencv.org/downloads.html)

---

### Post by bapoumba on 2014-07-03
[http://packages.ubuntu.com/trusty/digikam](http://packages.ubuntu.com/trusty/digikam)
digikam is in universe and does not show opencv as a dependency, thus my question. If the Trusty package too old, there is a ppa : [https://launchpad.net/~msylwester/+archive/digikam](https://launchpad.net/~msylwester/+archive/digikam)

---

### Post by MickSulley on 2014-07-03
Thanks for that, I had not come across ppa's before.

I have installed and that gets me from Digikam 3.5 to 4.0, which is a great improvement.  Is there any way to get to 4.1 which was released 30th June?  The link suggests that it would be 4.1 for trusty but it has installed 4.0

Thanks
Mick

---

### Post by bapoumba on 2014-07-03
Which Ubuntu release are you running ?

---

### Post by mc4man on 2014-07-03
> **MickSulley said:**
> Thanks for that, I had not come across ppa's before.

I have installed and that gets me from Digikam 3.5 to 4.0, which is a great improvement.  Is there any way to get to 4.1 which was released 30th June?  The link suggests that it would be 4.1 for trusty but it has installed 4.0

Thanks
Mick

You're getting 4.0 from the ppa because 4.1 failed to build (opencv version too old
Possibly the ppa will attempt to fix by providing a newer opencv though there could be other considerations.
(- a newer  opencv may break other apps that use it's libs.

---

### Post by bapoumba on 2014-07-04
Thanks mc4man, I had a look the yesterday and was not sure.

---

### Post by MickSulley on 2014-07-04
Sorry for the delay in replying, I am on 14.04

Yes as I understand it DigiKam 4.1 needs libkface which in turn needs OpenCV 2.4.9

---

