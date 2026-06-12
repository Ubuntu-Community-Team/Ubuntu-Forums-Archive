---
title: "Android Jellybean Ubuntu mounting problems"
date: 2013-01-18
forum: General Help
---

### Post by Jimstehrman on 2013-01-18
Hi all,
 
It seems that my ubuntu 12.04 will not properly mount my Samsung Galaxy S3 phone with Android 4.1 Jelly Bean.
The phone is basicallt brand -new with no modifications, and I've tried the following things to no avail:
 
- connecting via mtp: Can see file structure (Music, Pictures, Android folders), however the conents of these folders are not found (they all appear empty)
 
- connecting via ptp: Can see the file structure as above, and the folders within them, however most of those display as empty. I can see image and text files no matter where they are, but any audio file is not displayed
 
- I followed this guide ([http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/)), I had some strange outputs when I ran the commands
 
```

*mtp-detect | grep idVendor*
*mtp-detect | grep idProduct*
```
 
Which did not yield the code output suggested from the guide. Further, the output it did produce seemed to suggest that the mtp was recognizing the phone as both a Galaxy tab and a Galaxy nexus strangely enough.
 
- I then followed this guide ([http://blog.itsbilal.com/index.php/2012/12/connect-an-android-4-0-phonetablet-to-ubuntu-the-reliable-way/](http://blog.itsbilal.com/index.php/2012/12/connect-an-android-4-0-phonetablet-to-ubuntu-the-reliable-way/)) Which just didn't work. Here I did not encounter any errors, and it all seemed to go fine, until I tried connecting. An error appeared basically saying the device could not be found.
 
I can't seem to find anything else that looks hopeful. Has anyone else had this issue/know of a fix? Thanks.

---

### Post by mc4man on 2013-01-18
Don't have any such phones but just noticed a gvfs update in 13.04 that mentioned something about, was connected to this bug
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/903422](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/903422)

(if so then atm only fixed in the upcoming 13.04

---

