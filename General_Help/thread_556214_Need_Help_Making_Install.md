---
title: "Need Help Making Install"
date: 2007-09-21
forum: General Help
---

### Post by Angelbeast on 2007-09-21
Hi. I am trying to install Pixel I downloaded the 64 bit demo in tar.bz2 format. I think i am close but still missing something. Can someone walk me through this?

I have unpacked the files to a Pixel folder onto the desktop. I see in the folder a config.def file. Is that the one that i need to check the dependencies? 

I opened up a terminal window and changed the directory to the Pixel folder gave it a go. Here is the input and output from the terminal.

ron@ron-laptop:~/Desktop/Pixel$ ./config.def
bash: ./config.def: Permission denied

Waht am i doing wrong? I included a screen shot so you can see what files are in the folder.

---

### Post by Maestro23 on 2007-09-21
> **Angelbeast said:**
> Hi. I am trying to install Pixel I downloaded the 64 bit demo in tar.bz2 format. I think i am close but still missing something. Can someone walk me through this?

I have unpacked the files to a Pixel folder onto the desktop. I see in the folder a config.def file. Is that the one that i need to check the dependencies? 

I opened up a terminal window and changed the directory to the Pixel folder gave it a go. Here is the input and output from the terminal.

ron@ron-laptop:~/Desktop/Pixel$ ./config.def
bash: ./config.def: Permission denied

Waht am i doing wrong? I included a screen shot so you can see what files are in the folder.

Compiling from Source. You need "build-essential" installed.

> sudo apt-get install build-essential

Install that, then proceed with the instructions.

If it needs any more files(dependencies), it will tell you, then you must install them as well.

---

### Post by bigbrovar on 2007-09-21
try typing   this in terminal  ** sudo -i**   the would make u root then u can now   **./config.def**
try it and let me no the result

---

### Post by jocko on 2007-09-21
I don't see any source files in there. Have you tried running the actual program? It may already be compiled.```
./pixel
```

---

### Post by Angelbeast on 2007-09-21
Okay i tried all three suggestions with no luck. 

It said 'build-essential' was already installed.

Then i tried the other two and got this output:

root@ron-laptop:/home/ron# cd /home/ron/Desktop/Pixel
root@ron-laptop:/home/ron/Desktop/Pixel# ./config.def
bash: ./config.def: Permission denied
root@ron-laptop:/home/ron/Desktop/Pixel# ./pixel
./pixel: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory
root@ron-laptop:/home/ron/Desktop/Pixel#

---

### Post by jocko on 2007-09-21
The error you get while trying to run "./pixel" indicates that you need to install some other packages.

Go back to the page where you downloaded it and read what else you need to install to get it working.

Edit: the missing file (libcups.so.2) is in the package libcupsys2.
Find it in synaptic, or:
```
sudo apt-get install libcupsys2
```
You'll probably get a new error, if need to install more packages.

---

### Post by Angelbeast on 2007-09-21
ron@ron-laptop:~$ sudo apt-get install libcupsys2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcupsys2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Angelbeast on 2007-09-21
> **jocko said:**
> The error you get while trying to run "./pixel" indicates that you need to install some other packages.

Go back to the page where you downloaded it and read what else you need to install to get it working.

Edit: the missing file (libcups.so.2) is in the package libcupsys2.
Find it in synaptic, or:
```
sudo apt-get install libcupsys2
```
You'll probably get a new error, if need to install more packages.

good call...i'mback at the site now and i do need more packages...i'll give it nother try and let you know what happens

---

### Post by Angelbeast on 2007-09-21
kay these packages i could not find in synaptic:

freetype
icms
sane-backends


where can i find them?

Oh and here is wht it says on the pixel site:

Pixel 1.0 Beta 7 build 699 for Linux/x86/64cmpt, Multilanguage (2007-09-15)

Requirements: This is a 32-bit version of Pixel for Linux, it is compiled in special way to allow users of 64-bit processors to run it without problems in compatibility mode.

Please verify that you have following libraries installed: freetype, libsdl, lcms, sane-backends, cups, libpng, aspell and openexr.

Please visit FAQ section of this website to learn more about installing this version in mixed 32/64-bit environment.

---

### Post by jocko on 2007-09-21
> **Angelbeast said:**
> kay these packages i could not find in synaptic:

freetype
icms
sane-backends


where can i find them?

Oh and here is wht it says on the pixel site:

Pixel 1.0 Beta 7 build 699 for Linux/x86/64cmpt, Multilanguage (2007-09-15)

Requirements: This is a 32-bit version of Pixel for Linux, it is compiled in special way to allow users of 64-bit processors to run it without problems in compatibility mode.

Please verify that you have following libraries installed: freetype, libsdl, lcms, sane-backends, cups, libpng, aspell and openexr.

Please visit FAQ section of this website to learn more about installing this version in mixed 32/64-bit environment.

These are my guesses:
freetype is probably libfreetype6
lcms is probably liblcms1
sane-backends may be libsane, not sure...

---

### Post by Angelbeast on 2007-09-21
Okay i had all of what you had listed...i tried again...

root@ron-laptop:/home/ron# cd /home/ron/Desktop/Pixel/
root@ron-laptop:/home/ron/Desktop/Pixel# ./config.def
bash: ./config.def: Permission denied
root@ron-laptop:/home/ron/Desktop/Pixel# ./pixel
./pixel: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

---

### Post by jocko on 2007-09-21
I tried running it myself.
It looks like it requires that you have 32 bit versions of those files it complains about, and they need to be in the /usr/lib32/ directory.
You can get some of them by installing "ia32-libs", but some (like libcups.so.2 and a few more) you'll have to get somewhere else.

To see exactly which files are missing, run this in a terminal while you are in your Pixel/ directory:
```
ldd pixel
```
That will list all libraries needed to run the program and indicate which are missing.
I haven't tried, but I guess you can simply copy the missing 32 bit libraries from a 32 bit live cd session, or [download the 32 bit .deb files]("http://packages.ubuntu.com/"), extract them with the archive manager and copy from there...

---

