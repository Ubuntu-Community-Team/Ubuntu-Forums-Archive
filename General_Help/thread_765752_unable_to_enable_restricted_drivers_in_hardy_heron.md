---
title: "unable to enable restricted drivers in hardy heron"
date: 2008-04-24
forum: General Help
---

### Post by YonyonJohn on 2008-04-24
Hey, everyone,

I'm having a problem enabling the restricted nvidia drivers from the hardware drivers window. every time I try to enable the drivers, Ubuntu says I need to reboot, so I do, but the drivers still wont work. enabled is checked but it still says that it's not in use. has anyone else had this problem?

thanks in advance :)

screen shot:

[IMG]http://i31.tinypic.com/13z1bp.png[/IMG]

---

### Post by Devilotx on 2008-04-24
I've got the same issue, plus everything is so damn slow due to it being release day, I'm going to re-try things when the furor dies down a half step.

---

### Post by Next Turn on 2008-04-24
Same here, and I notice I can't use any desktop effects, probably because of the driver problem. Didn't have any issues in beta. Using GeForce 7900GTX. Is there any way to force in the old driver? Or maybe driver is okay, just a glitch in the full release.

---

### Post by lyricmuse on 2008-04-24
Not sure if this is the same problem, but I had the same issue when I first installed 8.04

My first install went without a hitch.  I took the chance and installed onto an external usb drive.

I installed with these exact steps:

1.  Base Ubuntu 8.04 
2.  Installed restricted drivers (Nvidia)
3.  Rebooted and ran all updates

Perfect install...

On my second install:

1.  Base Ubuntu 8.04
2.  Ran all updates
3.  Installed restricted drivers

and, to make a long story short, i had many problems enabling the restricted Nvidia driver.
So....
I did another install, based on my first perfect install, and it was perfection once again.  Maybe give that a shot, it seems to have worked for me.

Hardware Specs:
Architecture:  64 bit
Motherboard:  Intel 945GNT
Processor(s):  Pentium 4  3gHz HT
Video:  Palit 8600GT Super+ 1GB (excellent inexpensive card)
Memory:  4 Gbyte DDR2
Soundcard:  Diamond XtremeSound - 7.1/24 bit Sound Card
Hard Drive:  160 GB Maxtor Sata 3

---

### Post by Islington on 2008-04-24
same exact problem here too. I am reinstalling gutsy, since the servers are painfully slow.

---

### Post by datagrim on 2008-04-24
I had the same issue.  I just installed EnvyNG and it took care of it.

---

### Post by YonyonJohn on 2008-04-24
lyricmuse,

I installed the restricted drivers before updating as well, but it didn't work for me. glad to hear everything is working smoothly for some people though.:)

---

### Post by lyricmuse on 2008-04-24
> **YonyonJohn said:**
> lyricmuse,

I installed the restricted drivers before updating as well, but it didn't work for me. glad to hear everything is working smoothly for some people though.:)
What are your hardware specs?  I know I had a huge problem with other distros not understanding my graphics card and wide screen monitor.

---

### Post by the_darkside_986 on 2008-04-24
Once the server calmed down, I was finally able to do
```

sudo apt-get update
sudo apt-get install nvidia-glx-new

```
It helps to have the network interface enabled during installation so that it can "scan" the mirrors and you wouldn't have to worry about sudo apt-get update and Restricted Drivers should function as in previous versions.

---

### Post by Islington on 2008-04-24
How does one have the network interface enabled? 

I too got it to work as the server cooled off for a minute or two..

---

### Post by YonyonJohn on 2008-04-24
hey everyone, I figured it out!

here's how to get it working:

1) enable all the repositories
* go to system > administration > software sources
* check all boxes under downloadable from the internet
* go to the third - party software tab and check both boxes (this step may not be necessary)
* click close and reboot

2) update repositories
* go to system -> administration -> synaptic package manager
* click reload in the top left (this will take a while, make sure you let it finish)
* close close synaptic package manager and reboot

3) install drivers
* go to system -> administration -> hardware drivers
* the enabled check box should now be un-checked
* check the enabled check box next to the driver you are having problems with
* click enabled on the window that will come up
* reboot


that should fix it, not bad for a linux noob huh?

I'm going to go get screen shots to add to this

---

### Post by Devilotx on 2008-04-25
I've reinstalled 6 times, and I've discovered this:

Installing via the full booted Live CD and the Restricted manager works perfectly.

Installing via the X Installer (the live installer without the full live CD) and Restricted manager doesn't work.

it's also pretty repeatable.

I've got an AGP Nvidia 7600GS

---

