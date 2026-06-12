---
title: "gtkpod from source with aac - can't find mp4v2"
date: 2005-10-30
forum: General Help
---

### Post by uopjohnson on 2005-10-30
using Breezy with multiverse and universe enabled.
I'm trying to build gtkpod from source with aac support because I cannot find the gtkpod-aac binary referred to by several others...
When I try and build gtkpod from source it claims it cannot find the mp4v2 libs even though they are installed (dev too).  
there is no compile time option in gtkpod to explicitly set the location of the mp4 libs so I can't get around this that way.  I also rebooted and ran ldconfig, all to no avail.  
I'm new to ubuntu, but not to linux.  Any help would be appreciated.

---

### Post by JLTB on 2005-11-21
I've got the same problem, and the CVS build won't work either.  Anybody have any ideas?

---

### Post by uopjohnson on 2005-12-16
Ok well I got this working.  (Finally had a reason to look at it again)
What I did was build mp4v2 from source as well and then everything worked.
Here are my steps:
```

sudo apt-get remove gtkpod libmp4v2-0
sudo apt-get build-dep libmp4v2-0

```
download and untar libmp4v2-0
```

./autogen.sh
make
sudo make install

```
you may get an error during autogen.sh that you need to install some stuff.  I was able to get it all with apt-get install stuff... I'm not sure why these things don't come up in build-dep, but I think it is because the autogen.sh builds a bunch of other stuff as well as libmp4
if that goes well then you should be able to build gtkpod 
```

./configure
make
sudo make install

```
At the end of ./configure you should now see that it is being built with mp4v2 support and now everything is gravy!  
oh one more thing for some reason ldconfig (which loads shared libraries) was not looking in /usr/local/lib which is where libmp4v2 got put.  You may need to edit /etc/ld.so.conf and add /usr/local/lib so that it will be searched.  then run
```
sudo /sbin/ldconfig
```
to get everything in place.  You will know if this step is necessary because gtkpod will not start and wll give the error
"gtkpod: error while loading shared libraries: libmp4v2.so.0"
Hope that helps someone.

---

### Post by Evandenerley on 2005-12-18
Im also having problems with libmp4v2-0 but when i try the code posted above i get

evan@ubuntu:~/Desktop/gtkpod-0.99.2$ sudo apt-get remove gtkpod libmp4v2-0
Reading package lists... Done
Building dependency tree... Done
Package gtkpod is not installed, so not removed
The following packages will be REMOVED:
  gstreamer0.8-faac libfaac0 libmp4v2-0 libmp4v2-dev
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2429kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 73611 files and directories currently installed.)
Removing gstreamer0.8-faac ...
Removing libfaac0 ...
Removing libmp4v2-dev ...
Removing libmp4v2-0 ...
evan@ubuntu:~/Desktop/gtkpod-0.99.2$ sudo apt-get build-dep libmp4v2-0
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for faad2
evan@ubuntu:~/Desktop/gtkpod-0.99.2$ sudo apt-get libmp4v2-0
E: Invalid operation libmp4v2-0
evan@ubuntu:~/Desktop/gtkpod-0.99.2$ sudo apt-get build-dep libmp4v2-0
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for faad2

any one have ideas so i can get videos finally working

---

### Post by uopjohnson on 2005-12-18
You need to make sure that you have the universe repository enabled.

---

### Post by Evandenerley on 2005-12-19
ok that fixed the install problem but im having a hard time finding the file libmp4v2-0.tar.gz is it a part of another file or am i just blind.

---

### Post by uopjohnson on 2005-12-20
The website is here:
[http://mpeg4ip.sourceforge.net/]("http://mpeg4ip.sourceforge.net/")
you can download it from 
[http://prdownloads.sourceforge.net/mpeg4ip/mpeg4ip-1.4.1.tar.gz]("http://prdownloads.sourceforge.net/mpeg4ip/mpeg4ip-1.4.1.tar.gz")

---

### Post by Evandenerley on 2005-12-20
thanks the install went off without a hitch. although i do have the acc installed it wont accept .mp4 s but will accept .m4v files. if anyone knows of a good codec for .avi to .m4v that would be very useful

---

### Post by Evandenerley on 2005-12-21
id like to note that i used videora ipod on my windows partition to convert my .avi s to .mp4 s. i dont know how to use ffmpeg so if someone could write the code to change .avi to .m4v or .mp4 that would be great.

---

### Post by sinaen on 2006-10-06
thanks   many times over and over. now i can get my audio-books on to my ipod :D

 I Wonder if amaroK also have mp4 playback now :) 

yeah!! 
btw i did not have to remove the packages gtkpod and libmp4v2-0 as you said

---

