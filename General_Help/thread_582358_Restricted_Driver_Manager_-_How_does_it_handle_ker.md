---
title: "Restricted Driver Manager - How does it handle kernel modules?"
date: 2007-10-19
forum: General Help
---

### Post by JohnPhys on 2007-10-19
Hey everyone,

I was wondering if someone could tell me how the restricted driver manager compiles kernel modules and such.  Specifically, why does it require a reboot when enabling the nvidia drivers?  Don't you just have to "modprobe nvidia" and restart X?  I know you don't need a reboot in debian when using the module assistant.  

I ask because I want to see how the new compiz stuff works in gutsy on my desktop from the livecd (so I can't really restart to enable the driver).  I went to a tty to enable the nvidia kernel module, but it didn't seem to have been compiled yet?

Any ideas?

--John

---

### Post by DagMan on 2007-10-20
have you tried stopining gdm, installing the package, editing the xorg file to make sure the driver is nvidia and the color depth is 24, killall compiz, then restart gdm... this is how I *THINK* it might work on an installed box without a reboot but I'm not sure.  Also I'm not too sure that compiz runs on the Live CD so maybe opening a terminal and running compiz from there if you have to.

There's also some things that other people have needed doing to get compiz running, issuing a command that automagically adds to the xorg.conf file, but it's not always the case.

I don't know if that above will work but good luck.

I almost forgot, the restricted driver manager isn't needed for nvidia I think... I've had it disabled and NVIDIA drivers running fine but they were drivers from the NVIDIA site and not the repo ones.

---

### Post by JohnPhys on 2007-10-20
Yes, I've stopped gdm and restarted it, haven't stopped compiz (it's not running since the first driver that loads is the 2D nv one).  The LiveCD will indeed run compiz just fine, as I ran it on my laptop (intel graphics) last night.  xorg.conf also looked good (had "nvidia" for the driver and the correct color depth).

The reason I think it has to do with the modules is that I can't even get X to start up (forgetting about compiz completely) after telling it to use the nvidia driver, and the nvidia.ko kernel module is nowhere to be found.

Any ideas?

---

### Post by DagMan on 2007-10-20
have you tried to rmmod nvidia ; modprobe nvidia
compiz I think actually still runs when the xserver is killed but maybe that's not correct.  It was the behaviour of it in Ubuntu a while back. I think compiz is the script that sets up the window manager and runs it with whatever options, and compiz.real is the actual  binary that compiz calls as the window manager, but that the compiz script is still persisting after the graphics are killed.

---

### Post by DagMan on 2007-10-20
Additionally, I just got to thinking that, with the above so far
ctl-alt-f1
killall compiz
sudo /etc/init.d/gdm stop
sudo rmmod nvidia 
sudo apt-get install nvidia-glx or possible nvidia-glx-new or nvidia-glx-legacy, depending on the card... or download a driver from the NVIDIA website and install it if you plan to also do this after the install.
sudo modprobe nvidia
sudo nano /etc/X11/xorg.conf and see that things look okay

then this would be new
sudo /etc/init.d/linux-restricted-modules-common start <--the only option that does anything is start 


compiz &
sudo /etc/init.d/gdm start


Or something like that.  There may be some there that is not necisarry or that will error but none that is harmful.

---

### Post by JohnPhys on 2007-10-23
I'll have to give that a try, but I'm not sure why compiz would need to be killed, since I don't think it starts up anyway (on my desktop with the nvidia card it defaults to off).

I'll try it out later and let you know how it goes.

---

### Post by JohnPhys on 2007-10-23
Yeah, it fails at the "modprobe nvidia" part, it says it can't locate the kernel module, it just doesn't exist.  Very very odd.

Again, this is all from the live cd, so I'm not sure how that affects things.

---

