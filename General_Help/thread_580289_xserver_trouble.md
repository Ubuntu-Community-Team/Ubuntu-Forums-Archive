---
title: "xserver trouble"
date: 2007-10-18
forum: General Help
---

### Post by prow on 2007-10-18
i just updated to gusty..restarted the computer and poof xserver wont load.  so i did
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

...i think i put in the right options...nothing

is there anything else i can check?

im really not sure what options to put in the xserver-xorg config

---

### Post by Pumalite on 2007-10-18
Accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by prow on 2007-10-18
failed to load module "vesa" (module requirement mismatch, 0)
No drivers available

Fatal server error:
no screens found
X10: fatal IO error 104 (connection reset by peer) on x server ":0.0" after 0 re......

---

### Post by prow on 2007-10-18
also get
xauth: error in locking authority file /home/prow/.Xauthority

---

### Post by prow on 2007-10-19
bump

---

### Post by LanDan on 2007-10-19
> **prow said:**
> also get
xauth: error in locking authority file /home/prow/.Xauthority 

thats your problem! i guess you left your /home partition intact????

remove that file,
sudo rm  /home/prow/.Xauthority
and do a startx

---

### Post by prow on 2007-10-20
> **LanDan said:**
> thats your problem! i guess you left your /home partition intact????

remove that file,
sudo rm  /home/prow/.Xauthority
and do a startx

i dont understand what your talking about....what is Xauthority?
i actually just got extremely frustrated and just did a clean install.
but still please explain more about the Xauthority....that way i'll know for next time
i have a huge suspicion that im going to to feel like a HUGE n00b after you tell me

---

### Post by g2g591 on 2007-10-20
xauthority is X's way of knowing if its already running, if its already there it thinks its already running and so doesn't start.

---

### Post by LanDan on 2007-10-21
its just a verry small file that can be deleted and that might give a problem once every upgrade

but OK! i i think a re install also works ;)

a noob? well yes actualy, but let me tell you 1 thing, if something doesn't work in Linux it will always ive you an error message of some sort and you are never the first one with that problem.

if you would have googled with your error message you probable would have found a post from me 4 years ago on linuxquestions.org asking the same NoOb question ;)

---

### Post by prow on 2007-10-22
> **LanDan said:**
> its just a verry small file that can be deleted and that might give a problem once every upgrade

but OK! i i think a re install also works ;)

a noob? well yes actualy, but let me tell you 1 thing, if something doesn't work in Linux it will always ive you an error message of some sort and you are never the first one with that problem.

if you would have googled with your error message you probable would have found a post from me 4 years ago on linuxquestions.org asking the same NoOb question ;)

well thanks guys....i'll remember this for next time.

---

