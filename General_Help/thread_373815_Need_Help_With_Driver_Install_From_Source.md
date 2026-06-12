---
title: "Need Help With Driver Install From Source"
date: 2007-03-01
forum: General Help
---

### Post by ibohren on 2007-03-01
Hello Everyone,

I posted for some help yesterday locating a Linux driver for my older Visioneer OneTouch 7600 USB scanner. After some digging, I was able to find a driver at 

[http://viceo.orcon.net.nz/](http://viceo.orcon.net.nz/)

but it's in source code form. I am still very new to Linux and bash scripting, and I'm not sure how to take the source for this driver and install and implement it. It says it supports Sane 1.0.9. I have Xsane installed and I'm running Ubuntu 6.10. Does anyone know if this driver will work with Xsane, and if so, can someone walk me through in beginners terms how to install and implement this driver? There are usage instructions on the site above, but they are a bit advanced and beyond my understanding at this point.

Thanks a ton in advance for any help or suggestions!

---

### Post by rsambuca on 2007-03-01
Silly question, but have you tried just starting xSane and seeing if the scanner is detected?

---

### Post by Maestro23 on 2007-03-01
If what rsambuca told you to try doesn't work....

If the file is a tar.gz file, you will need the tar command.  In terminal:

> tar -xvf filename.tar.gz

This will extracted the file and create a new directory.  Inside that directory will be a README and/or INSTALL doc.  It will contain instructions on how to install.  Compiling a program from source can get tricky and messy for someone new to linux.

I know off the top of my head, you will need to have "build-essential" installed even before you try to compile the driver.

In terminal:

> sudo aptitude install build-essential

Take those steps and post back your progress.

---

### Post by ibohren on 2007-03-01
Yeah, right after I posted I thought I might be asked that. I did, and it does not detect the scanner.

Thanks :)

---

### Post by rsambuca on 2007-03-01
To get the file, you will have to right-click the link on the website and select "Save Link As..."

---

### Post by Maestro23 on 2007-03-01
> **rsambuca said:**
> To get the file, you will have to right-click the link on the website and select "Save Link As..."

Hey rsam, if you have anything to add to what I posted, chime in.  I might have missed something.:)

---

### Post by ibohren on 2007-03-01
OK, I did that and it saved it to my desktop as a .diff.gz file:

e3_driver_0.6.diff.gz

What should I do with it?

Thanks

---

### Post by Maestro23 on 2007-03-01
> **ibohren said:**
> OK, I did that and it saved it to my desktop as a .diff.gz file:

e3_driver_0.6.diff.gz

What should I do with it?

Thanks

Start with the step I posted above.

Get to your Desktop first:

> cd /home/username/Desktop

---

### Post by ibohren on 2007-03-01
Maestro23,

I did what you suggested. I extracted the gz file and the only thing it contained is the file

e3_driver_0.6.diff

No read me or install instructions. I also tried installing Build Essentials as you suggested. I ran the command in the terminal and it ran through the install, but the program doesn't show in my applications tab with my other installed applications. Can I find launcher somewhere else?

Thanks

---

### Post by Maestro23 on 2007-03-01
> **ibohren said:**
> Maestro23,

I did what you suggested. I extracted the gz file and the only thing it contained is the file

e3_driver_0.6.diff

No read me or install instructions. I also tried installing Build Essentials as you suggested. I ran the command in the terminal and it ran through the install, but the program doesn't show in my applications tab with my other installed applications. Can I find launcher somewhere else?

Thanks

Hmm... Just found these instructions over at the site(Under Usage link):

> Hopefully the process of patching both SANE and the kernel have now been simplified

   1. Patch your kernel with the supplied file to enable the E3 and E4 support
   2. Install the updated scanner.o file into your modules directory and "modprobe scanner"
   3. Download the 1.0.9 sane backend and unpack
   4. Patch the source with the supplied diff file from the download directory

            gunzip -c e3_driver_0.6.diff.gz | patch -p1 
   5. Now build and install the sane release as normal
   6. Once build try "scanimage -L" to see if it detects your scanner
   7. If this fails type "export SANE_DEBUG_VIDEO=128" and retry the above
   8. Also refer to the FAQ page for more tips on debugging
   9. Note you will still need some support files as detailed in the 0.4 notes below



---

### Post by ibohren on 2007-03-01
Yes, but they're beyond my comprehension level at this point:

   1. Patch your kernel with the supplied file to enable the E3 and E4 support
   2. Install the updated scanner.o file into your modules directory and "modprobe scanner"
   3. Download the 1.0.9 sane backend and unpack
   4. Patch the source with the supplied diff file from the download directory

            gunzip -c e3_driver_0.6.diff.gz | patch -p1 

   5. Now build and install the sane release as normal
   6. Once build try "scanimage -L" to see if it detects your scanner
   7. If this fails type "export SANE_DEBUG_VIDEO=128" and retry the above
   8. Also refer to the FAQ page for more tips on debugging
   9. Note you will still need some support files as detailed in the 0.4 notes below

It sounds like I need more that just the driver. This is everything listed with the driver download:

    * E3 Driver patch Release 0.6 - Supports Sane 1.0.9
    * e1.ini and lut.plg and viceo.conf support files - Updated
    * Kernel 2.4.17-19 scanner.c/h patch file including Erik Strack stability changes.
    * Kernel 2.4.17-19 scanner.c/h patch file.

I have downloaded and extracted all of them. I now have the driver, a folder containing support files (but still now Read Me or Install instructions), and what appears to be 2 versions of a kernel scanner file.

Thanks

---

### Post by Maestro23 on 2007-03-01
Yeah, its going to get messy.  Those are the instructions, but they assume you know your way around the terminal and command line/linux file structure.  I have got to leave the boards for awhile.  Hopefully someone will see your post and give you a hand.  I'm bookmarking your post, and when I get back tonight, I will check in on you.

Good luck man.

---

### Post by ibohren on 2007-03-01
Maestro23, 

Thanks for your help so far. I'll keep trying. I've been fumbling around with the instructions and was getting the sense that it was going to be difficult as well. I don't know how to patch my kernel and build an install yet, hopefully someday. The page with the driver hasn't been updated since 2002 and only states that it supports sane backend 1.0.9, and I'm only finding backends back to version 1.0.14 on sane's website. If I could figure out how to do this, could I even assume that this driver would work with a current sane backend?

Thanks again!

---

### Post by magichsjx on 2007-06-09
actually i have a similar problem i am trying to install a webcam driver, the Kensington SVGA webcam that went out of business in 2001 and I found a driver foor the webcam to work on Ubuntu dating from the same year. I unpacked the .tar.gz file and got a new folder, went in there and did a make but got errors. they had a .diff file so i tried to patch the kernel but the code is written for the 2.4 kernel not 2,6(using Dapper). I dont know i tried the patch -1 xxx.diff command but it is just hanging and dont know if it's going anywhere. I thought since you guys were on the same topic maybe you could give me an idea what I am doing wrong or anything at all. good luck to all:)

---

