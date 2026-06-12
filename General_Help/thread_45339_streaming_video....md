---
title: "streaming video..."
date: 2005-06-29
forum: General Help
---

### Post by DarkManX4lf on 2005-06-29
ive recently install ubuntu and upon installing it i have recieve TONS of problems, so here is one of them how can i get streaming video in mozilla firefox to work ? i followed the ubuntu starter guide to get mplayer plugin for firefox and i got it installed ok, but when i try to play a streaming video like from [www.gamespot.com](www.gamespot.com) it wont work i can hear audio but no video....when i go to cbs.com and try to watch some streaming news videos from there it has to launch totem to play it......but when it launches totem it gives me an error saying "resource busy or unavailable" its NOT running i have checked the system monitor.....

i cant get the flash player plugin for mozilla firefox.... i modify my /etc/apt/sources.list and add the new and "extra" repositories like it says in the starteguide....and then i type

apt-get update
apt-get install flashplayer-mozilla

and it says this:

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) hoary/java Packages (/var/lib/apt/lists/ubuntu.tower-net.de_ubuntu_dists_hoary_java_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package flashplayer-mozilla


.....i dont get it....


and then when i try to get the program Limewire to install (like the starter guide says), i follow the starter guide and ihave to install sun-j2re1.5 so i type:

apt-get install sun-j2re1.5 

and guess what !!!! :

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) hoary/java Packages (/var/lib/apt/lists/ubuntu.tower-net.de_ubuntu_dists_hoary_java_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5

amazing....as a new linux user comming from windows, i find windows much better....but i really woudl like to give linux a more chances....so can someone help me with these problems?

---

### Post by DarkManX4lf on 2005-06-29
also here is my sources.list


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted



i have tried many other peoples sources.list from this forum none of them help me..and i should add that i tried to use synaptic for these packages and they are not listed there.

one more thing, I am on a FRESH install of ubuntu **AMD 64** and the only thing that i have done so far was install xine, mplayer and installed my ati drivers as well as mount my windows partitions.

---

### Post by DarkManX4lf on 2005-06-29
here is what i get when i try to stream videos in firefox


[[IMG]http://img215.echo.cx/img215/5794/screenshot2qm.png[/IMG]](http://www.imageshack.us)


thats all i see, no where do i see video but i see that mplayer box.

---

### Post by DarkManX4lf on 2005-06-30
bump

---

### Post by tzutolin on 2005-06-30
[QUOTE=DarkManX4lf]bump[/QUOTE]
 I have similar problem using mplayer-plugin in firefox too. The progress bar usually just load at one third and then stop.

---

### Post by crashtest on 2005-06-30
[QUOTE=tzutolin]I have similar problem using mplayer-plugin in firefox too. The progress bar usually just load at one third and then stop.[/QUOTE]

I've had some success following the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=44560) , which explains how to install the 2.85 version of mozillaplug-in.  Read through the whole thread before trying this, because there are actually 2 howto's in the thread.  For some reason, I can only get streaming media to work in Mozilla 1.78, not in Firefox.  I'm sure it will get worked out eventually.

---

### Post by DarkManX4lf on 2005-06-30
thanks i will go try it out.

---

### Post by DarkManX4lf on 2005-06-30
nope it doenst work i follwed the guide, both guides on that  thread and none ofthem help, i tried it in both firefox (amd65 v1.0) and regular mozilla 1.78, in firefox i can hear audio  but no video, in mozilla 1.78 when i try to stream video it asks me to install  plugin either from apple/WMedia/realplayer etc.....

---

### Post by DarkManX4lf on 2005-06-30
bump

---

