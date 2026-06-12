---
title: "Can't instal w32codecs in my X86 Gusty"
date: 2007-11-24
forum: General Help
---

### Post by astomi on 2007-11-24
Follow by below method:
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

 sudo apt-get install w32codecs

The error shows:

[COLOR="Red"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate[/COLOR]

Then I download 

w32codecs_20071007-0medibuntu1_i386.deb 

sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

The error is 

[COLOR="Red"]
dpkg: error processing w32codecs_20071007-0medibuntu1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 w32codecs_20071007-0medibuntu1_i386.deb
[/COLOR]

---

### Post by skyjacker on 2007-11-24
> **astomi said:**
> Follow by below method:
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

 sudo apt-get install w32codecs

The error shows:

[COLOR="Red"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate[/COLOR]

Then I download 

w32codecs_20071007-0medibuntu1_i386.deb 

sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

The error is 

[COLOR="Red"]
dpkg: error processing w32codecs_20071007-0medibuntu1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 w32codecs_20071007-0medibuntu1_i386.deb
[/COLOR]You could check the info. on this link and see if that would help you.

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

---

### Post by forestpixie on 2007-11-24
I think you need to get 64 bit version but I can't find anythng - other than threads saying it's not done yet - try searching for w32codec and 64 bit

Edit - no i lied try to install non-free-codecs

```
sudo apt-get install non-free-codecs
```
 this is the synaptic description

> Non-free codecs
This package depends on the binaries codecs package matching your architecture
(w32codecs for i386, w64codecs for amd64 and ppc-codecs for powerpc systems).

---

### Post by rsambuca on 2007-11-24
You want the w64codecs, although you really don't need them for much these days.  Have you installed the gstreamer codecs already?

---

### Post by astomi on 2007-11-24
I have installed gstreamer already, my purpose to install the w32codecs is that can play AVI,RMVB format video.

---

### Post by astomi on 2007-11-25
can anyone help me play the RMVB in  AMD64 GUSTY?

---

### Post by FuturePilot on 2007-11-25
Have you installed the w64codecs? Those are also in the Medibuntu repo. It's the 64bit equivalent of w32codecs

---

### Post by astomi on 2007-11-25
Yes,I follow your advice to install w64codecs, but it still can't play rmvb format video.

---

### Post by FuturePilot on 2007-11-25
What media player are you using? Usually Mplayer or Vlc can play just about anything.

---

### Post by astomi on 2007-11-25
I use Mplayer, now I can play rmvb file.
That's because the rmvb file name is chinese ,then I change to english name it is OK.

But Mplayer screen flash , maybe lost frame and I try other rmvb video with the same problem

---

