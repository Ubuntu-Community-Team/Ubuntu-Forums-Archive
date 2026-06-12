---
title: "Cannot unzip a  .tbz file"
date: 2017-03-30
forum: General Help
---

### Post by bask185 on 2017-03-30
I am following this tutorial: [https://wiki.qt.io/RaspberryPi_Beginners_Guide](https://wiki.qt.io/RaspberryPi_Beginners_Guide). I am stuck at the step where I need to unzip this file 
tar -xf gcc-4.7-linaro-rpi-gnueabihf.tbz

The tutorial said I had to download a special 32 bit package thingy, so I apt-get installed it which seemed it was working.
But than I still could not unzip the .tbz file.

I downloaded the file using: ```
wget https://www.dropbox.com/s/sl919ly0q79m1e6/gcc-4.7-linaro-rpi-gnueabihf.tbz
```

this is the error message I am getting:
```
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now
```

I really need to complete this really really bad Qt tutorial...

---

### Post by howefield on 2017-03-30
Looks like a corrupt download or file. I'd suggest downloading direct from sourceforge as indicated in the tutorial. 

The file should be around 90 MB large, how large is the dropbox file that you downloaded ?

---

### Post by bask185 on 2017-03-30
I tried both the download links more than 1 time, both are 208K large

EDIT: the scourgeforge one is 33K

---

### Post by steeldriver on 2017-03-30
Yeah it looks like the "sourceforge" link actually redirects to an intermediate html page that eventually links to the sourceforge page

I suggest you open the link in a browser and follow the download links from there

---

### Post by howefield on 2017-03-30
Sorry to hear that, seems to work for me albeit downloading via the browser not wget.

```
cd Downloads
```
```
ls
gcc-4.7-linaro-rpi-gnueabihf.tbz
```
```
tar -xf gcc-4.7-linaro-rpi-gnueabihf.tbz
```
```
cd gcc-4.7-linaro-rpi-gnueabihf/
```
```
ls -al
total 1508
drwxr-xr-x 8 hugh hugh    4096 Mar 30 14:07 .
drwxrwxr-x 4 hugh hugh    4096 Mar 30 14:07 ..
drwxr-xr-x 7 hugh hugh    4096 Aug  8  2012 arm-linux-gnueabihf
drwxr-xr-x 2 hugh hugh    4096 Aug  8  2012 bin
-rw-r--r-- 1 hugh hugh 1508968 Aug  8  2012 build.log.bz2
drwxr-xr-x 3 hugh hugh    4096 Aug  8  2012 include
drwxr-xr-x 3 hugh hugh    4096 Aug  8  2012 lib
drwxr-xr-x 3 hugh hugh    4096 Aug  8  2012 libexec
drwxr-xr-x 9 hugh hugh    4096 Aug  8  2012 share
```

---

### Post by bask185 on 2017-03-30
yeah this worked, tnx. Never thought that this would happen to me on Ubuntu :(

---

### Post by howefield on 2017-03-30
Glad you got it but the issue is nothing to do with the operating system.

---

