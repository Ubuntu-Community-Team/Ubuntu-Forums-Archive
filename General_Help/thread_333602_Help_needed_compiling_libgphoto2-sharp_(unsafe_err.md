---
title: "Help needed compiling libgphoto2-sharp (unsafe error)"
date: 2007-01-07
forum: General Help
---

### Post by ntetreau on 2007-01-07
Hi, 
I am trying to get banshee (0.11.3) up and running with MTP support for my creative zen microphoto.  I am following the guide [here]("http://www.banshee-project.org/Guide/DAPs/MTP/CompileGPhoto2").

Unfortunately, I cannot compile libgphoto2-sharp.  Supposedly, it cannot find the "unsafe" command. 

The actual output is:

```
libgphoto2-sharp-2.3.0$ make
Making all in src
make[1]: Entering directory `/home/nt271/temp/libgphoto2-sharp-2.3.0/src'
sh ./testsizes-createsource.sh csharp < testsizes-typelist.txt > TestSizes.cs
make  all-am
make[2]: Entering directory `/home/nt271/temp/libgphoto2-sharp-2.3.0/src'
unsafe -debug -out:libgphoto2-sharp.dll /target:library AssemblyInfo.cs ./Camera.cs ./CameraAbilitiesList.cs ./CameraFile.cs ./CameraFilesystem.cs ./CameraList.cs ./CameraWidget.cs ./Context.cs ./ErrorCodes.cs ./Object.cs ./Port.cs ./PortInfo.cs ./PortInfoList.cs
/bin/bash: unsafe: command not found
make[2]: [libgphoto2-sharp.dll] Error 127 (ignored)
make[2]: *** No rule to make target `libgphoto2-sharp.dll.mdb', needed by `all-am'.  Stop.
make[2]: Leaving directory `/home/nt271/temp/libgphoto2-sharp-2.3.0/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/nt271/temp/libgphoto2-sharp-2.3.0/src'
make: *** [all-recursive] Error 1

```

Any help appreciated!

Nic

---

### Post by ntetreau on 2007-01-10
Turns out I needed to install mcs (mono compiler).  Unfortunately, banshee with mtp borks out when I plug in my creative zen... oh well back to amarok!

Nic

---

### Post by rockrhino27 on 2007-01-27
I'm going to try compiling libgphoto2-sharp myself right now.  I'll let you know if I make out well.  

Rich

---

### Post by rockrhino27 on 2007-01-27
Well I managed to compile the library just fine.  I compiled banshee from source just fine also, compiled in the mtp support.  When I plug in the Zen banshee does nothing.  Gnome lets me know that a camera has been detected, but my only option is to import photos.  When you click on that button it commences to download everything on the Zen.  I'm talking to a few guys in the banshee chat room on irc.gnome.org, so if I find anything out i'll respond to this thread.  :confused: 

Rock

---

### Post by organica on 2007-01-29
> **rockrhino27 said:**
> Well I managed to compile the library just fine.  I compiled banshee from source just fine also, compiled in the mtp support.  When I plug in the Zen banshee does nothing.  Gnome lets me know that a camera has been detected, but my only option is to import photos.  When you click on that button it commences to download everything on the Zen.  I'm talking to a few guys in the banshee chat room on irc.gnome.org, so if I find anything out i'll respond to this thread.  :confused: 

Rock

Yes, please reply if you find something out.  MTP support (and *reliable* professional video editing) are the last features I need to be stable in order to wipe the Windows partition off my computer.  At least I could get one knocked out if MTP works well!

---

### Post by fictivetoast on 2007-02-09
I've got a Creative Zen Vision M, and after building everything from source using the banshee guides
here: [http://www.banshee-project.org/Guide/DAPs/MTP](http://www.banshee-project.org/Guide/DAPs/MTP)
and here: [http://www.banshee-project.org/Guide/DAPs/MTP/CompileGPhoto2](http://www.banshee-project.org/Guide/DAPs/MTP/CompileGPhoto2)

I'm very happy to report that banshee is up and speaking with my Zen player!
most important was being sure that gphoto could read the player, otherwise banshee wouldn't either.  if "gphoto -L" returns a full happy list of files, you're set.  

I had to manually edit the list cap, by going to libgphoto2-2.3.1/libgphoto2 in the source tree and editing gphoto2-list.c to change MAX_ENTRIES from 1024 to 12000 so it wouldn't cough.. but it's been golden after that.

---

### Post by ntetreau on 2007-02-11
Thanks fictivetoast, changing the max entries fixed the problem for me.  However, reading the file list takes enormous amount fo time compared with libmtp, any idea why or how to fix this?

Nic

---

