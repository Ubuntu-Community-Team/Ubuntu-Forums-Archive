---
title: "help getting fglrx working in feisty!"
date: 2007-05-18
forum: General Help
---

### Post by Atrio05 on 2007-05-18
ok i just tryed to install the fglrx driver and now i'm stuck i checked the /var/log/Xorg.0.log file for errors and it says at the very bottom (EE) No Devices Detected  and  Fatal server error: no screens found. and when i try to start x it says about the same thing.

i have an ATI Radeon 7000/VE video card and i'm trying to get svideo out to work so thats why i wanted to install the fglrx driver.

i really need some help please as of right now i cannot use that computer because x is broken!!


HELP!!!!!!!!!!!!! :( :(

---

### Post by Atrio05 on 2007-05-20
can some one give me a little help here i kinda need to use that computer.

---

### Post by bobplano on 2007-05-20
you can switch it back to ati drivers via nano or sudo-dpkg-reconfigure xserver-xorg. what does fglrxinfo put out?

---

### Post by Atrio05 on 2007-05-20
i'll have to get back to you on exactly what it says tomorrow but it basically says it cannot find any screens.

---

### Post by Ub1476 on 2007-05-20
Hi there:)

Just follow this Howto thread I created: [Linky]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

When Ubuntu is installed you'll start totally clean, no need to download driver before it's properly installed

Oh, and you don't need to reinstall, just edit the xorg.conf file as described. Please leave a comment in the thread to bump it:biggrin:

Cheers, Ub

---

### Post by Atrio05 on 2007-05-20
ok that didn't work at all. i am not having aproblem installing fiesty i am having a problem trying to get the fglrx driver to work properly.

---

### Post by Atrio05 on 2007-05-21
do you need me to type in exactly what the error says?

---

### Post by aldenhg on 2007-05-22
With your card you're probably better off with the radeon driver. The easiest way to switch is to first remove fglrx:
```
sudo apt-get remove xorg-driver-fglrx
```
Then edit your xorg.conf file:
```
sudo nano /etc/X11/xorg.conf
```
And then replace the part that says 
```
Driver       "fglrx"
```
with 
```
Driver       "radeon"
```
Restart and it will probably work. The fglrx driver isn't very well maintained and often breaks older cards. The OSS driver (radeon) has made some leaps and bounds recently, especially with older cards. If you want really good Linux support you should pick yourself up an Nvidia card. I made the switch from a Radeon 9800 Pro to a GeForce 7600GS and not only does everything work really, really well with Nvidia's drivers, but it also required no configuration besides installing the driver.

---

### Post by jocko on 2007-05-22
> **Atrio05 said:**
> i have an ATI Radeon 7000/VE video card and i'm trying to get svideo out to work so thats why i wanted to install the fglrx driver.


fglrx does not support cards older than radeon 9500.
I think the only way to get tvout from older cards is to patch the open source driver.
Check [this page]("http://wiki.cchtml.com/index.php/Tvout").

---

