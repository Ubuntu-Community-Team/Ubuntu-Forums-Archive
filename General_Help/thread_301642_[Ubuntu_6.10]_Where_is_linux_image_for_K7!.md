---
title: "[Ubuntu 6.10] Where is linux image for K7?!"
date: 2006-11-17
forum: General Help
---

### Post by Gondor on 2006-11-17
Hi!

I had Ubuntu 6.10 installed but i can't install kernel for K7 processor.

This is my source.list (post here because i can't upload :-k )

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe




I have another problem: nvidia driver don't work.
The command "nvidial-glx-config enable" write on console: "Error: unable to load nvidia kernel driver! Be sure to have installed the nvidia driver for your running kernel."

Output uname -r:
> 2.6.17-10-386

These are the packages installed:
[http://gondor.netsons.org/immagini/linux_image_k7_01.gif](http://gondor.netsons.org/immagini/linux_image_k7_01.gif)
[http://gondor.netsons.org/immagini/linux_image_k7_02.gif](http://gondor.netsons.org/immagini/linux_image_k7_02.gif)


Help, i can't use my nvidia driver card :sad:

---

### Post by machoo02 on 2006-11-17
In this release the developers have tuned the 'generic' kernel to be optimized for both i686 and k7 type processors.  Just use the generic kernel, and all will be well (at least for your kernel woes...I can't help you with the nvidia problem).

---

### Post by Gondor on 2006-11-17
> **machoo02 said:**
> In this release the developers have tuned the 'generic' kernel to be optimized for both i686 and k7 type processors.  Just use the generic kernel, and all will be well (at least for your kernel woes...I can't help you with the nvidia problem).

ok thanks :)


Someone for the nvidia problem? :mrgreen:

---

### Post by RFScheer on 2006-11-17
I recommend Automatix to deal with your nvidia driver.  Just google to the Automatix web site and follow instructions.  Very easy way to get EVERYTHING working well in Edgy.

If you are unable to get a gui screen with your existing setup, you might want to change the proprietary nvidia driver to the generic nv driver in your xorg.conf file and that should give you a screen at least.

CTL-ALT-Backspace will restart the X server with your new config.  

This is easy to do and I'll be happy to help if you don't understand this.

---

### Post by Gondor on 2006-11-17
> **RFScheer said:**
> I recommend Automatix to deal with your nvidia driver.  Just google to the Automatix web site and follow instructions.  Very easy way to get EVERYTHING working well in Edgy.

If you are unable to get a gui screen with your existing setup, you might want to change the proprietary nvidia driver to the generic nv driver in your xorg.conf file and that should give you a screen at least.

CTL-ALT-Backspace will restart the X server with your new config.  

This is easy to do and I'll be happy to help if you don't understand this.

Thanks! Problem resolved :KS

---

