---
title: "Internet connection died, gnome wont start as a result"
date: 2007-03-25
forum: General Help
---

### Post by robophred on 2007-03-25
I am using the hurd (hutch?) 5 install, as the others would not use my monitor correctly.

I noticed previously that when I had my internet cable unplugged, gnome took ages to do anything, had many programs crash on startup, and wouldn't run any others.

Somehow, a recent patch killed my internet connection.
Now I am stuck with a rather useless computer...

It might have somthing to do with me removing dhcp3, as I had to install it and a few other things to get a network boot for the laptop I am currently using.  The problem is I cant reinstall it to see if it works, as the problem itself is no internet connection.

This has happened occasionally before, I just crashed gnome, went to another tty, and did startx, which seemed to recover the internet connection and run fine.  This time, it isnt working.

Seems if I wait long enough (20 minutes to an hour), gnome will start up successfully, although the deskbar applet crashes and everything still runs painfully slow.  I can start firefox and access my router, but anything beyond that wont connect.

Previously, I fixed a problem like this (this seems to happen semi-often) by going into the internet connection controls and finding that the dhcp host box was erased.  I cannot do that this time, as starting either the control panel or the terminal will just say "starting" for a while, then shut down (occasionally crashing compix.real).  Strangely, I can successfully start the desktop effects controls, and it runs fine and fast, but when I turn it off and close the box, the effects are still active for a while.


Update: desktop effects finally shut down, and I was able to get the control panel open and get to the network settings box.  Everything in it is correct...

---

### Post by bulldog on 2007-03-25
As I read your story,I get the strong idea there's something wrong with your laptop's hardware.

If you haven't a connection with the internet,it won't affect the performance of Feisty because it's just running from the hdd.

I should check if DMA is enabled to get a better performance.

---

### Post by bettlebrox on 2007-03-25
Sounds like the loopback interface isn't up. Can you post the contenst of these files:

/etc/network/interfaces
/etc/hosts

---

### Post by robophred on 2007-03-25
I was able to get it running again by crawling my way to the network settings box and re-adding the dns ips.

The problem still exists where the computer runs insanely slow without an internet connection (I can remove the cable to start it running slow, and plug it in again and see the speed return).
I would like to solve this, as my internet is off during the night.  It would be nice to fix the problem rather than having to crash gdm and start x manually every time (which does seem to get around it on occasion, as mentioned in the first post).

This is on my main computer, the laptop is what I was using to get the internet connection.

/etc/network/interfaces
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



/etc/hosts
> 
127.0.0.1 localhost
127.0.1.1 robophred-desktop.tc.ph.cox.net

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


I have read about the loopback issue on the forums.  That doesn't seem to be what is going on here, but may be similar.  If the computer will slow to a crawl without the loopback, then it is probably doing so without the main connection on my computer.

---

### Post by bettlebrox on 2007-03-25
Make a copy of /etc/hosts and change these lines:

127.0.0.1 localhost
127.0.1.1 robophred-desktop.tc.ph.cox.net

To this:

127.0.0.1 localhost robophred-desktop.tc.ph.cox.net
127.0.1.1 robophred-desktop.tc.ph.cox.net

See this blog posting for more info:

[http://www.formatds.org/a-little-optimization-tip-for-ubuntu/](http://www.formatds.org/a-little-optimization-tip-for-ubuntu/)

---

### Post by ypout on 2007-07-16
I am having the exact same problem, did the suggested local host changes work for you?

---

