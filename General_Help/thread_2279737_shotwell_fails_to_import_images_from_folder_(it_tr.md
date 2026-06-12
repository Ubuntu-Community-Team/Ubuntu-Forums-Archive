---
title: "shotwell fails to import images from folder (it tries to overwrite source images)"
date: 2015-05-25
forum: General Help
---

### Post by B._Bogart on 2015-05-25
I have some images from my Canon S5 IS I was unable to mount via PTP  on this up to date Trusty machine, so I used a memory card reader and  copied the files to a local directory. I'm importing with "import from  folder" and selecting "copy" rather than "import in place". All the  input files are seen, but none are imported.


 The error log shows entries like the following:
 couldn't copy /home/bbogart/tmp/images/IMG_0201.JPG
 to /home/bbogart/tmp/images/IMG_0201.JPG
 error message: Error creating directory: Permission denied


 This seems to indicate that the source and destination are the same  (source) filename, and the import fails due to trying to overwrite the  files in place.


 Why would shotwell be trying to copy the files to the source  location? My photos are in ~/Photos and this is properly set in the  preferences.

I've also submitted this issue as a bug report: [https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/1458085](https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/1458085)

---

### Post by B._Bogart on 2015-06-04
Solved. Somehow Shotwell changed my library directory!

---

