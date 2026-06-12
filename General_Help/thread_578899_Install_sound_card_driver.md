---
title: "Install sound card driver"
date: 2007-10-17
forum: General Help
---

### Post by pack74743 on 2007-10-17
I am new to Linux and Ubuntu, having installed 7.10 just a few days ago.  I have never had any sound whatsoever, and last night, with the help of this forum It was determined that my sound card (Creative SoundBlaster X-Fi) is not recognized.  I was also helped here in determining that no drivers for this card are yet available.

With that determination I decided to give up on Ubuntu, at least for the time being, until a driver becomes available.  However, today I went to the Creative support site and found what I believe to be drivers for my sound card for both Windows and Linux.  I installed the new Windows driver and it works fine.

I also downloaded the Linux driver and it is now sitting on my desktop.  The name and file type are XFiDrv_Linux_US-1.04.tar.gz.  I also extracted the contents and that folder is also on my desktop so that I can deal with either one once I know what to do.

What I now need desperately is detailed instructions on how to install the driver (assuming that it might be the correct driver).  There is a ReadMe in the driver folder which states:

===================================================================


  "Sound Blaster X-Fi Linux x86_64 Beta Driver Readme File


  September 2007


====================================================================


The purpose of this document is to describe how the X-Fi Linux device 

driver is built, packaged, and released.



Quick install


=============


1) You must have the fully configured source for the Linux kernel and 

   ALSA which you
 want to use for this device driver. Partial installed 

   kernels (e.g. From distribution makers) may be unusable for this 

   action.


2) Run one of the following commands as root in the terminal:

   ./installer     OR
   

   ./installer --with-alsainc=<ALSA_include_directory>

  * ALSA Source Tree

 
   On 2.6 kernels, the location of the ALSA source include directory


      is parsed automatically from the running kernel.


      If it is not in the standard place, specify the path via

   
   --with-alsainc=<ALSA_include_directory>.



     On 2.4 kernels, the location of the ALSA source include directory


      must be specified via --with-alsainc=<ALSA_include_directory>.


  * Note

      If integrated ALSA is to be used to build, --with-alsainc option


      must not be specified."

(None of which I understand.)  Please help me.  Thank you!

pack

---

### Post by ckamc on 2007-10-22
bump, if someone could help explain it a little it would be great since I too have the same card :)

---

### Post by Atriach on 2007-10-23
I'm in the same boat, hopefully some help comes soon.  I tried double-click the installer, and then selecting run in terminal.  That is what the directions seem to be implying, though in a different way.  That didn't work for me though.

---

### Post by tim heeter on 2007-10-23
I'm in with you two. Although this issue was addressed in another forum.

[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

I have yet to try the walkthrough but it looks promising from what I can tell. Best of luck.

---

### Post by jocko on 2007-10-23
Have you tried doing what the readme tells you to do?

In a terminal (assuming the name of the extracted folder is XFiDrv_Linux_US-1.04 and is located on your desktop):
```
cd ~/Desktop/XFiDrv_Linux_US-1.04/
./installer
```You may need to install a few extra packages, like build-essential and linux-headers-generic to get it to work.

---

### Post by tim heeter on 2007-10-23
I haven't tried any option as of yet. I'm about to leave work, but I'll give that a shot and post my results if I am successful or not. I was having trouble installing it last night as it was returning me with the error of I am not running a 64 system. But I am.

---

