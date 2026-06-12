---
title: "getting webcam working is impossible"
date: 2007-01-05
forum: General Help
---

### Post by PetePete on 2007-01-05
i was given a "mikomi M6219" webcam for christmas and its probably utter shite but i'd still like to get it working on my computer which is seeming to be a bit tricky.

i've already searched various pages for driver support but found non, is there a generic webcam driver i can try installing?

I've installed, camstream, gqcam, ov511-source, pwc-source and webcam but nothing seems to pick it up. I think the problem is that nothing is being sent to /dev/video

any ideas?

---

### Post by Cholito on 2007-01-05
$ apt-cache show spca5xx-source

---

### Post by PetePete on 2007-01-05
thanks, i installed the package (sudo apt-get install spca5xx-source), restarted but still no luck :(

is there anything else i needed to do?

---

### Post by Zaggy on 2007-01-05
You might want to try out easycam, easycam2 and motion.
I use that in combination with apache to use my Logitech webcam.
Haven't had any luck with getting it to work in IMs like Gaim, Kopete or aMSN

---

### Post by PetePete on 2007-01-05
i'll give them a try. 

I also noticed i dont have any video devices in my dev folder.
so no /dev/video or /dev/video0

used mknod to create a video0 but no help, and its been removed after i restarted :S

---

### Post by PetePete on 2007-01-05
i installed easycam2 and it said that no webcam was found, or incompatiable webcam

guess i should just give up :(

---

### Post by patrickfromspain on 2007-01-05
Check what dmesg says about...

---

### Post by fragos on 2007-01-05
With Edgy you should be using gspcav1-20061216.tar.gz as your webcam driver.  It can be found at [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

---

### Post by tomchuk on 2007-01-06
Just a quick note about *-source packages...
They won't actually do you any good unless you compile them with your kernel. You'll want to install module-assistant and do:
```

# this will install build deps for building a kernel module for the running kernel
m-a prepare
# this will build a .deb specific to the running kernel and install it
m-a a-i <whatever>-source

```

---

### Post by mdurham on 2007-01-06
make sure that you use the USB socket on the computer and not an external hub as I did. It won't work on an external hub, a fact that took me ages to discover.
Cheers, Mike

---

### Post by smoker on 2007-01-06
i got mine working with camorama, available in synaptic

---

### Post by PetePete on 2007-01-06
i downloaded gspcav1-20061216.tar.gz but couldn't find any newbie friendly guide to installing it (or any guide for that matter?!) so i took a guess with 

make

then sudo make install

seemed to do something (there was no configure file though) but maybe i have to do something else after?

(then found the file gspca_build so ran that as root and restarted, but nothing)

restarted the pc, tried plugging the webcam back in and same errors when loading webcam or gqcam (no /dev/video or /dev/video0 )

thanks so much for the help!

---

### Post by fragos on 2007-01-06
Make sure the permisions for gspca_build include ececute and run "sudo ./gspca_build"

---

### Post by PetePete on 2007-01-06
yes it was executable and it seemed to run sucessfully. Think its a case of the webcam not working with the drivers.

---

### Post by fragos on 2007-01-06
The developer's site has a list of supported webcams.  After checking that you could email him and ask a question.  He did respond to me on an issue I had with hid site.

---

### Post by d3v1us on 2007-06-16
this is what i get when i run:  sudo ./gspca_build

-----
m0sd3v@th3b0x:~/m0sd3v/Moz DLed/gspcav1-20070508$ sudo ./gspca_build 

 REMOVE the old module if present

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/m0sd3v/m0sd3v/Moz DLed/gspcav1-20070508 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** No rule to make target `DLed/gspcav1-20070508'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2
------

(sorry for my noobness)

i also was unable to install EasyCam2 or 1.
any help would be greatly appreciated!

---

### Post by fragos on 2007-06-16
d3v1us -- In ~/m0sd3v/Moz DLed/gspcav1-20070508 look at kgspca.err.  My guess is you need to install linux-headers-2.6.20-16-generic with Synaptic.  Always search in Synaptic for packages before compiling them yourself.

---

### Post by d3v1us on 2007-06-16
i should have learned the first time this happened to me..

it always simplifies things to leave out spaces when naming folders--by deleting the space in the Moz DLed folder name, i had no trouble installing.

btw, i did have linux-headers-2.6.20-16-generic installed.

thanks!  :)

---

