---
title: "Plz Help installing Usbvision driver"
date: 2004-11-09
forum: General Help
---

### Post by neon on 2004-11-09
I'm trying to install the usbvision driver ([http://usbvision.sourceforge.net/](http://usbvision.sourceforge.net/)) in ubuntu. The driver has a make file but when I do "make" this error occurs:
"
+make -C /lib/modules/2.6.8.1-3-386/build SUBDIRS=/home/neon/usbvision-0.9.7/src modules
make: *** /lib/modules/2.6.8.1-3-386/build: No existe el fichero o el directorio.  Alto.
                                                                                                                             "
Translation: the /lib/modules/2.6.8.1-3-386/build directory doesnt exist

Any suggestions?

Please help me 'cause I've been weeks trying to make my tv-card (hauppauge wintv usb) work.  #-o 

Thanks and sorry for my english  :D

---

### Post by ubuntu-geek on 2004-11-09
I believe all you need todo is install the kernel headers package installed.

sudo apt-get install linux-kernel-headers

You might also want the build tools..

sudo apt-get install build-essential

Hope that helps.

---

### Post by neon on 2004-11-10
Thanks ubuntu-geek I've just done that but I still get the same problem. :cry: 
Any other suggestions?

---

### Post by newbsawbit on 2006-10-29
I had the same problem,

I googled this :

make: *** /lib/modules/2.6.15-27-686/build: No such file or directory

and found this :

[http://ubuntuforums.org/showthread.php?t=274845](http://ubuntuforums.org/showthread.php?t=274845)

Different device, but he seemed to have the same problem - 
he said:

"Well I've ansewered my question but I'm still having no success.
I needed the package linux-headers-2.6.15-27-686"

So I decided to try:

	'sudo apt-get install linux-headers-2.6.15-27-686'

and it worked! woohoo!

Not that your probably still fooling with it as this post is 2 years old, but for anyone else that comes across this post in their struggle as I did.
I am using a Nogatech USB-TV FM (NTSC), feel free to contact me.

---

