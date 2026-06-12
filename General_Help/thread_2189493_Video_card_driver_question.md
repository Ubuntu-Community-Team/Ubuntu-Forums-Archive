---
title: "Video card driver question"
date: 2013-11-22
forum: General Help
---

### Post by wolfen10862 on 2013-11-22
I have a older Emachine T508 duel core 3 gig processor 2 gig of ram and a Nvidia Graphics card
Right now its useing X.org xserver-noveau display driver from xserver-xorg-video-noveau ( open Source)

I want to use a different video driver but I'm terminal phobic (still, but learning) so I try to install Nvidia binary xorg driver, kernal module and VDPAU library from nvidia-331 ) open source) 
or another ( proprietary) if possible to make my video card work better and increase my frame rat in World of tanks, but every time I select "apply changes" in the software and updates, it asks for my password so I input the password and then it does nothing, what am I doing wrong

---

### Post by mellocode on 2013-11-22
I hate to say this but in the terminal can you run ```
sudo apt-get install nvidia-current
``` and post the output

---

### Post by wolfen10862 on 2013-11-22
did it and it says the following:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Could it be that I need to download the driver from Nvidia and put it somewhere first?

---

### Post by mellocode on 2013-11-22
Do you have Ubuntu Software Center or the Additional Drivers windows open? If so close them and re-run.

---

### Post by wolfen10862 on 2013-11-22
Nothing was open when I ran the terminal, I even restarted the computer just in case to make sure

---

### Post by CatKiller on 2013-11-23
Did you have some kind of package manager crash? If you absolutely definitely don't have a package manager running and you still get that message you can delete the lock file mentioned in the error message and try again.

---

### Post by wolfen10862 on 2013-11-23
Nope no package installers were running.

BUT, this is what I did late last night

I re downloaded Ubuntu 13.10 from a different source, burned it onto a disk, this morning I re installed Ubuntu using the top option where it saves my settings and files, upon completion I went to the software and updates icon in settings and clicked n the additional drivers tab, just to see before I came back here again, I checked the box for 
:using NVIDIA binaryXorg driver,Kernel module and VDPAU library from nvidia-319 ( proprietary tested):
It went really really slow compared to the rest of Ubuntu, so one of the things happened, (1) I didn't install Ubuntu correctly the first time, (2) I fixed it with the reinstall (3) it was installing all the time and Linux is just usually so fast I thought it wasn't installing 
Also I no longer have the 331 showing up yet so either it will come with the next update or I'll do without it, no biggie if I don;t get 331 had that on windows and the Nvidia game center was not comparable with this old T5082

---

