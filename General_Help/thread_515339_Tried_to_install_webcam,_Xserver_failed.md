---
title: "Tried to install webcam, Xserver failed"
date: 2007-08-01
forum: General Help
---

### Post by pankus on 2007-08-01
I was testing out my new webcam in linux, I downloaded gspcav1 from here: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) , 
went
tar
make
make install
modprobe gspca

when I restarted, X had failed and told me that I didn't have an appropriate screen, reverting to an old version of xorg.conf didn't help. I'm running ubuntu 7.04. Help me, I have no idea what to do, I am a linux noob.

---

### Post by zidane2 on 2007-08-01
type sudo dpkg-reconfigure xserver-xorg

this should get gui

---

### Post by patrimesa on 2007-08-01
HI

my webcam comes embedded, the laptop's an HP dv 1000, and I don't know how to make it work! can you help me out? and please be as specific as possible! I get easily lost in this new to me UBuntu language...

thanx!

---

### Post by pankus on 2007-08-01
Okay I tried the dpkg-reconfigure, but I still get the same error about an API mismatch and that there are screens, but none that are suitable.

---

### Post by pankus on 2007-08-01
Fixed it! Installed the nvidia drivers again after downloading from their website.

---

