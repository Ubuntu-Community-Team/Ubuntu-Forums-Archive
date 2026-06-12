---
title: "GeForce 6150 SE n430"
date: 2014-02-22
forum: General Help
---

### Post by ericmark4 on 2014-02-22
&#65279;So as soon as I marked my thread Solved, the Nvidia driver follies kick in again, on my fresh install of Xubuntu 12.04. 

I spent days and days trying to fix this on my previous installation, before giving up and doing a clean re-install. Once that was up and running, things worked perfectly---until today. Now I am back to: When I boot, I get a command-line log in screen. When I run xfce4-start, I get a screen where the fonts and icons are screwy, all shut-down options except "log out" are grayed out and I clearly have no administrative powers. (Cannot authorize anything, even with my password.) 

Been here before....I have read and tried literally dozens of suggestions about how to "fix" the Nvidia/12.04 disconnect. Re-do headers, delete xconf.org, purge then re-install via Terminal, etc. None of them worked for me last time out; this time I want to take a more informed approach before I just bag (X) Ubuntu and go back to the Dark Side. 

For the record, I tried 13.10 and had a similar issue there: DVD playback simply would not work, despite trying many suggestions online....I recently got the Ubuntu/Linux mojo back. Years ago I used Lucid as my main OS for awhile and really liked it. I drifted back to Windows simply because chess is my main hobby and that's one area where Ubuntu has not caught up yet. 

Now I am truly sick and tired of M$ and will put up with more limited chess study resources for the sake of Ubuntian goodness---but these problems are really starting to drag me down. Is there an Idiot's Guide to Fixing Nvidia Hell that I missed in my search? My system runs GeForce 6150 SE n430 integrated graphics.
 
ALL advice much appreciated. Thanks much.

---

### Post by pqwoerituytrueiwoq on 2014-02-22
all you should need to do is run these commands on a clean install
```
sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot
```
using vga or dvi for your monitor?

you can try 14.04, it is almost at beta 1
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by ericmark4 on 2014-02-22
> **pqwoerituytrueiwoq said:**
> all you should need to do is run these commands on a clean install
```
sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot
```
using vga or dvi for your monitor?

you can try 14.04, it is almost at beta 1
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)


Thanks, but I have tried that--usually after a complete remove-purge and reboot first. I tried many many things....sorry if I sound frustrated, but I am. I had the Linux/Xubuntu mojo flowing big-time when I decided to ditch the Dark Side. This Nvidia thing with 12.04 is the worst problem I have faced on Linux, by far. There seems to be no clear answer. "The problem" manifests itself in different ways on different PCs. For instance: After my last post, I tried again to delete/purge all Nvidia anything. Then I installed the latest driver and nvidia-settings via Synaptic. It worked the first time I re-booted. The next time, not so much....back to the command line log-in, etc.

I know how LT felt when he let loose on Nvidia in the interview. Those of us with older GeForce 6-series graphics get hit especially hard, it seems. The last driver that supports the 6-series is 304, and the latest driver overall is 331. That adds to the mess.

I'm gonna go back to the Nouveau driver and deal with the loss of brightness and clarity. For now. Just cannot believe that after two years it is so hard to get Nvidia drivers and Precise to play nice. Bah....but thanks anyway.

---

### Post by pqwoerituytrueiwoq on 2014-02-22
if you are interested in nouveau you should give 14.04 a try, the modern kernels support nvidia cards better than they did 3 years ago
you should give the 3.14rc4 kernel a try when it comes out in a day or 2

you may need to boot using nomodeset in your kernel boot line with the nvidia driver, i have not needed to do that for a few years now, but i have been using modern nvidia chips (550 Ti/650 TI Boost)
oldest i have used in a 8200m, but your chip is well ancient by todays standards

---

### Post by egeezer on 2014-02-22
You need to run the 304 driver, which can be done as follows:
When you get the command-line login, do log in, and at the cursor run:
```
jockey-text --list
```
(you might have to use sudo, I don't remeber if I did)
That will take a while, and when it finishes you will have a list of the available drivers, most of which will be marked Disabled, with the exception being 331.
I believe you'll find 304 there - if you do, you can enable it with the command:
```
jockey-text -e (and the full xorg argument)
```
It would be well to run
```
man jockey-text
```
 to get the full options available.

---

### Post by egeezer on 2014-02-22
Back again with additional help: I gave you those instructions from memory, but here is a link to the actual sequence I used (a thread from these forums back in December):
[http://ubuntuforums.org/showthread.php?t=2193029&page=12&highlight=jockey-text](http://ubuntuforums.org/showthread.php?t=2193029&page=12&highlight=jockey-text)
The relevant post is #115

---

### Post by ericmark4 on 2014-02-23
> **egeezer said:**
> Back again with additional help: I gave you those instructions from memory, but here is a link to the actual sequence I used (a thread from these forums back in December):
[http://ubuntuforums.org/showthread.php?t=2193029&page=12&highlight=jockey-text](http://ubuntuforums.org/showthread.php?t=2193029&page=12&highlight=jockey-text)
The relevant post is #115

Thanks much. To tell you the truth, I tried several versions of the 304 driver, installed various ways: jockey, Synaptic, terminal. Either I am missing something obvious or anyone running 12.04 with Nvidia graphics---especially an older model---is dancing on the edge. Normally I would favor the former, but in this case....

For now I switched to 13.10. I figured out how to make DVD playback work and all is well, except that Moonlight won't work, as it did on 12.04. That's a small price to pay. If things continue smoothly I will likely upgrade to Trusty when the final version is released.

Fun stuff.

---

