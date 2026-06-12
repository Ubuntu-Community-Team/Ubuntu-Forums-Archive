---
title: "Logitech Quickcam Connect"
date: 2006-12-14
forum: General Help
---

### Post by ickleangel on 2006-12-14
Hey guys,

i been trying to install my new quickcam connect in ubuntu efty edge,

in device manager it will recognise the audio part but not the video,

i have EasyCam2 installed and that doesnt recognize it either, nor does Camorama or Ekiga Softphone.

i have looked through the forums and i believe it has something to do with /dev/video0 ?

im not sure because i only been using linux for about a week now, 

any help greatly appreciated,

thanks,

ike,

Comp Specs:

Acer TM2423Wxmi 1.5GB Ram 40GB HDD Ubuntu 10.0 Edgy Eft.

ike,

---

### Post by FluffyElmo on 2006-12-14
I don't have a Quickcam myself but this thread should help. It doesn't seem to be KUbuntu specific and should work. If you have any problems you can post here or there and we'll see what we can do.

[http://ubuntuforums.org/showthread.php?t=303330]("http://ubuntuforums.org/showthread.php?t=303330")

Good Luck!

---

### Post by fragos on 2006-12-14
Go to [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) and get [http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz)
This is the correct driver for Edgy.  The one refernced above is for older kernels.

---

### Post by ickleangel on 2006-12-15
> **fragos said:**
> Go to [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) and get [http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz)
This is the correct driver for Edgy.  The one refernced above is for older kernels.

the older one works for me, so do i need to uninstall that and how do i go about doing that? as i am new to linux.

thanks,

ike,

---

### Post by fragos on 2006-12-15
Place the gspca-20060930 tarball in whatever directory you wish.  Right click the tar ball and select to extract here.  A gspca-20060930 directory will be created.  Inside it is the gspcav1 directory.  Open a terminal and "cd" to that directory.  Normaly your run configure but this developer has gone to the trouble writing a bash script that does everything you need to do to install the directory.  Run "sudo gspca_buil" on the command line, responding with your personal password when asked.  Your done other than to select one or more web cam applications to run.  camerama is a simple one that works and the smartphone ekiga will also work but its a little trickier to configure.

---

### Post by ickleangel on 2006-12-15
thanks fragos, works great now, linux is actually really easy to use and install stuff glad i made the switch!.

thanks again,

ike,

---

### Post by mural on 2007-01-14
Hi ,

The latest drivrer for kernel up from 2.6.11 : gspcav1-20070110.tar.gz.  Will this work for amd64?
When I extracted it, I did not see a gspcav1 directory.  Help is appreciated.

---

### Post by fragos on 2007-01-14
> **mural said:**
> Hi ,

The latest drivrer for kernel up from 2.6.11 : gspcav1-20070110.tar.gz.  Will this work for amd64?
When I extracted it, I did not see a gspcav1 directory.  Help is appreciated.

There was an upgrade in a video library and for a while there were two versions of the webcam driver to work with them.  the latest version of the webcam driver is now compatitle with the old and new video libraries.  Since you're compiling it may work both 32 and 64 bit.  You could ask the author and or look in the readme files.

---

### Post by mural on 2007-01-14
Hello,

when I run  gspca_build, I get the following error message:

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/murali/Web Cam Driver/gspcav1-20070110 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `Cam'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2

Any idea?

---

### Post by fragos on 2007-01-14
gspcav1-20070110.tar.gz is a newer version than that I had so I installed tonight with problem.  I running 2.6.17-10-386 on an AMD 64.  One would think -386 and -generic would be the same and work on any x86 family processor.  Otherwise we're the same.  Ask the developer.  He helped me when I had a problem.  I can't offer any other suggestions.

---

### Post by opus on 2007-01-23
I had the same error as mural did.  I moved the extracted folder to the root of my home directory and ran it again and it worked.  It seems you can't have spaces in the folder path when you do the install.

opus

---

### Post by Zumlin on 2007-02-12
If have to admit that i am a real Linux newbe but i try my best.
So i tried to install this drivers  for my webcam as described above but it occurs a strange failure notice when i type in "sudo gspca_build". I always get the failure notice "sudo: gspca_build: command not found" but i am definitivly in the rigth directory and this file exits. :confused: 
Any suggestions? Do i have to compile anything first?

Sory for my broken englisch

---

### Post by FluffyElmo on 2007-02-12
Try *sudo ./gspca_build* from the directory it is in. If that doesn't work then try changing the permissions on the file to make it executable, *chmod 777 gspca_build* and then run the original command again...

---

