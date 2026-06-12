---
title: "Minitube hangs too much"
date: 2013-01-20
forum: General Help
---

### Post by Crisshome on 2013-01-20
Hello ,I have a problem with Minitube on Lubuntu 12.10.
It seems when I type something the searching goes for a long time about few minutes and when it finds the videos it even then I still have to wait a big deal to play them.


I never had this issue before with other distros.
My  compuer is AMD Athlon x64 3000+ 1.8GHz ,2GB Ram and Ati radeon 3400HD.
I can play 720p fine on youtube using either Firefox or Chromium.

So what gives?

---

### Post by black veils on 2013-01-23
i've never been able to get minitube working in any distribution, but recently this ppa of the latest version does:
**deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) quantal main**

---

### Post by Crisshome on 2013-01-23
So how do I install it?

---

### Post by black veils on 2013-01-23
i realise doing this will probably require manually fetching a key after.

```
sudo apt-get install synaptic
```open synaptic  >>  settings  >>  repositories  >>  other software tab  >>  add  >>  paste in the ppa line ***deb [COLOR=Black][http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu)[/COLOR] quantal main  ***>>  close

click the reload button at top-left to refresh everything. here is where the key error may occur, if so:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6D975C4791E7EE5E
``` replace that number code with your own stated in the error. it may or may not need a " at the end.

now you can search minitube in synaptic and install the latest version.

***if you want to remove it:***
software sources >> other software tab >> select the ppa then click remove button

---

### Post by black veils on 2013-01-28
there is a workaround also, for a gstreamer bug, which affects a few applications including minitube, try this:

32-bit

```
sudo mv /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```64-bit

```
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak

```"That's it, MP4 videos should now work under Ubuntu 12.04. There aren't any visible side effects to using this work-around, but in case you find one, you can simply rename **libgstvideoparsersbad.so.bak** back to **libgstvideoparsersbad.so**."

source: [http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html](http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html)

---

### Post by mc4man on 2013-01-28
> **black veils said:**
> there is a workaround also, for a gstreamer bug, which affects a few applications including minitube, try this:

source: [http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html](http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html)

That has been widely mis-reported as a good workaround when it was initally just a test & a semi acceptable workaround for a short time till issue was fixed in gst-bad.

Atm new packages aren't available in 12.04/10 though should be in the near future. A ppa for 12.04/10 was set up with fixed packages - look in the description here under "Current workaround:" for how - 
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)

---

### Post by black veils on 2013-01-28
> **mc4man said:**
> That has been widely mis-reported as a good workaround when it was initally just a test & a semi acceptable workaround for a short time till issue was fixed in gst-bad.

Atm new packages aren't available in 12.04/10 though should be in the near future. A ppa for 12.04/10 was set up with fixed packages - look in the description here under "Current workaround:" for how - 
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)

despite that, installing from included repository didnt work for me, and installing version 1.9 from ppa had freezing problems, until i did the work-around.. but its good to know about the linked ppa.

---

