---
title: "immigrant from suse could use a few tips"
date: 2007-07-09
forum: General Help
---

### Post by scorpion_gr on 2007-07-09
a)
I switched to kubuntu because suse produced severe crashes for no good reason. Of all the errors I still find some in kubuntu : when shutting down it can't power off on its own, switching to runlevel 1 (what seemed to be the only without X) produced a powered off screen and a still-powered tower and I had to reboot the hard way, same case if I opt for a console login at the graphic login prompt.

b)
I noticed there is no /etc/inittab file... is this normal ? How can I set a non graphic default runlevel in order to install the nvidia driver?

c)
How does the thing with the repositories work and what can I find there?
What is the binary filetype for installation packs here (like suse and redhat use .rpm)?
Any extra repositories with useful aplications and stuff I should add?

d)
Anything else I should  know?


PS.: I'm still a linux-n00b 8-[

---

### Post by tribaal on 2007-07-09
Hum debian based systems use runlevel 1 as single user, non-networking runlevel (if they boot through it at all, my *runlevel* output shows "N 2"). So basically, you have no real reason to leave runlevel 2 on Ubuntu. 

To get a non kdm console (what you get when switching to runlevel 1 on suse), just press <ctrl><alt>F1.
You'll need to terminate your graphical session with the following command : ```
sudo /etc/init.d/kdm stop
```
Then do whatever you want with the NVIDIA installer, and just restart your kdm by subsituing "stop" with "start" in the previous command :)

As for the package management system, it works quite differently. 
You don't want to download packages from your web browser (generally), but instead use apt-get or aptitude (in CLI), or "Synaptic" (GUI front-end, can be found in KDE's menu, but I'm unsure where exactly since I use GNOME :) ).
What it does is scan repositories for available packages/programs, and then if you select one to install it'll download it from a trusted Ubuntu server and install it automagically. In most cases, it'll create a shortcut in the system's menu for you.

There is extensive, more in-depth documentation available online if you would like more details. I suggest [Asyiu's collection of essays]("http://www.psychocats.net/ubuntu/index.php"), they are very well-written. If you're used to other linux systems, you will find some stuff that's too easy/already known, but it's a great ressource :)

Hope this helps :)

Don't hesitate to ask more questions :)

- trib'

---

### Post by scorpion_gr on 2007-07-10
How about this: other than graphic consoles, I can't bring ANY real console to life:

ctrl+alt+f1 produces a black screen (all black) and the cpu goes up... after a while I get an "out of range" frequency message from my screen and the system reboots (or tries to). Reading the threads it seems someone lost a couple of screens due to buntu's
 frequency settings...

Logging in directly to console (at the login prompt) produces a similar black uresponsive screen

booting into recovery mode just stalls with no apparent error messages and the cpu fan goes up again. 

:confused:

---

