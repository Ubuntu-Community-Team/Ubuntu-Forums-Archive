---
title: "upgraded from 1204 to 1210 no launcher or panel"
date: 2012-10-22
forum: General Help
---

### Post by hunterkasy on 2012-10-22
I have a dell Inspiron 537s 
dual core @ 3ghz
3 gigs of memory

just upgraded from 1204 to 1210 and the launcher and top panel does not show up at all

I need some help to solve this issue

thanks

---

### Post by daslinkard on 2012-10-22
> **hunterkasy said:**
> I have a dell Inspiron 537s 
dual core @ 3ghz
3 gigs of memory

just upgraded from 1204 to 1210 and the launcher and top panel does not show up at all

I need some help to solve this issue

thanks
[This]("http://askubuntu.com/questions/202752/unity-top-bar-side-bar-and-window-decorations-missing-after-upgrade-to-12-10/202782#202782") may be helpful for you!

---

### Post by hunterkasy on 2012-10-23
[http://askubuntu.com/questions/202752/unity-top-bar-side-bar-and-window-decorations-missing-after-upgrade-to-12-10/202782#202782]("http://askubuntu.com/questions/202752/unity-top-bar-side-bar-and-window-decorations-missing-after-upgrade-to-12-10/202782#202782")


I have tried several methods in the link above and nothing seems to help, can smeone help me on this one

---

### Post by oldfred on 2012-10-23
Do you have nVidia or AMD proprietary driver installed? Issue seems to be missing headers so proprietary driver is not  correctly installed.

Fix for nVidia with 12.10 missing kernel dpkg reconfigure:
[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

cntrl-alt f1 or f2 to get to terminal also works
sudo apt-get install linux-headers
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current
(Same for fglrx also)
sudo apt-get install linux-headers-generic fglrx-updates


Has most bug reports:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341)

[https://bugs.launchpad.net/fglrx/+bug/1068456](https://bugs.launchpad.net/fglrx/+bug/1068456)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)
[https://bugs.launchpad.net/fglrx/+bug/1068661](https://bugs.launchpad.net/fglrx/+bug/1068661)

Has what worked for me, install headers & dpkg update.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942)

When you see you are in the desktop but no icon or bar, right click to change desktop background
When the window appear, click all settings, now you see the system settings window.
Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD... fglrx-upgrade

---

### Post by hunterkasy on 2012-10-23
I have ati/amd vesa:rv710
 
when I go to the proprietary driver selection their is nothing to pick from it is empty

---

### Post by oldfred on 2012-10-23
I know installing headers works with nVidia. Some have posted it works with fglrx driver also, but that seems to depend on version of card.

Did you try command line updates?

---

### Post by hunterkasy on 2012-10-23
> **oldfred said:**
> I know installing headers works with nVidia. Some have posted it works with fglrx driver also, but that seems to depend on version of card.

Did you try command line updates?

I tried command line update I think their was around 8 updates that insalled

---

### Post by hunterkasy on 2012-10-23
is their any other options for me to try to get this fixed?

---

### Post by oldfred on 2012-10-23
I do not know about the other updates.

But:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic 
sudo apt-get install  fglrx-updates

---

### Post by hunterkasy on 2012-10-23
> **oldfred said:**
> I do not know about the other updates.

But:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic 
sudo apt-get install  fglrx-updates

I did the above the sudo apt-get install fglrx-updates was the only one that had a update, it install fine, but I have the same issue with no launcher or top panel

---

### Post by dino99 on 2012-10-23
open a terminal (ctrl+alt+T, or ctrl+T)

if you are using unity:

sudo dpkg-reconfigure unity

if you are using gnome-panel:

sudo dpkg-reconfigure gnome-panel

..... same story for other DE

or try:
gnome-panel --replace
unity --reset
gnome-shell --replace
....

---

### Post by hunterkasy on 2012-10-23
> **dino99 said:**
> open a terminal (ctrl+alt+T, or ctrl+T)

if you are using unity:

sudo dpkg-reconfigure unity

if you are using gnome-panel:

sudo dpkg-reconfigure gnome-panel

..... same story for other DE

or try:
gnome-panel --replace
unity --reset
gnome-shell --replace
....

I am using unity I tried sudo dpkg-reconfigure unity nothing happened even rebooted the computer still the same

---

### Post by hunterkasy on 2012-10-23
any other people have any ideas on what to do

---

### Post by bovender on 2012-10-23
I have no idea either, but I get the impression that a whole lot of people are affected by this. For me, none of the suggestions in the bug reports worked. I have the linux-headers installed, but no matter what driver I install, there is no Unity.

What's worse, I downgraded to 12.04.1, and Unity disappeared after the second reboot or so.

I'm now on Unity 2D...

---

### Post by Ace..... on 2012-10-23
> **hunterkasy said:**
> any other people have any ideas on what to do

I know this sounds like a cop out... but..........

I had terrible problems of exactly the sort you are having.

Days were spent trying to find a fix.
In the end, I was pointed to lesser known option by YannBuntu:

Re-install while keeping ones data and settings.

It's an honest 2hours work, but most of that is spent doing something else.
If you can't find a fix, you should definitely try it cos it's tried and tested.

Consider using a 12.04 disk for the re-install, until the probs are sorted in later versions.

The link is in my signature.
The guide is my step by step for noobs, but it contains the links to all the key resources you might need.

It's a decent last resort (or first resort if your stuck for time). ;)

---

### Post by hunterkasy on 2012-10-23
> **Ace..... said:**
> I know this sounds like a cop out... but..........

I had terrible problems of exactly the sort you are having.

Days were spent trying to find a fix.
In the end, I was pointed to lesser known option by YannBuntu:

Re-install while keeping ones data and settings.

It's an honest 2hours work, but most of that is spent doing something else.
If you can't find a fix, you should definitely try it cos it's tried and tested.

Consider using a 12.04 disk for the re-install, until the probs are sorted in later versions.

The link is in my signature.
The guide is my step by step for noobs, but it contains the links to all the key resources you might need.

It's a decent last resort (or first resort if your stuck for time). ;)


thanks for the info, I may have to do it this way, was hoping for a quick fix or a soon to be released update to fix this issue

---

### Post by hunterkasy on 2012-10-24
I want to thank everyone for the help,

Just wondering if anyone knows if thier is a bug fix committed for this issue and how soon could I expect one out for a update?

---

### Post by bovender on 2012-10-28
Here's an additional suggestion for those users who are missing the launcher dispite installing the linux-headers-generic package: What finally worked for me was to (re)move the .config directory in my home directory. Evidently some settings conflicted with the new driver/unity version. With .config moved out of the way, I got unity back.

**Careful:** If you attempt this solution for you, don't *delete* the .config directory as it contains your application settings. For example, I had to execute 'cp .config-old/libreoffice .config' to get my LibreOffice settings back.

---

### Post by stankopp on 2012-10-29
I have given up on 12.10 and re-installed 12.04.  How can this be released with these problems?  I have tried every suggestion in this and other thread without success.  It is this stuff that keeps Ububtu and Linux in general from becoming mainstream...

---

### Post by pedro.nariyoshi on 2012-10-29
I have an HD2400 and fglrx refuses to detect it (I think they've dropped support for the older graphics cards), try doing:
```
sudo modprobe radeon
```
On tty and see what happens. (Make sure to purge fglrx and fglrx-updates and xorg.conf before doing so).

Also, if your configuration is "messed". Try re-enabling unity-plugin on CompizConfigurationSettingsManager. (Or you might want to create a new user and see if Unity/Gnome-Panel work on that).

---

### Post by mvidberg on 2012-10-29
I am not having this particular issue as I do get the top bar and the side launcher bar BUT the side launcher bar only appears when I press the special window key on my keyboard.  Otherwise, moving the mouse over to the side does NOT make it come up (but perhaps this may be just a compiz-ubuntu setting somewhere that somehow got toggled).

Seems that for the people that can't get the bars to appear at all, it's probably because they got rid of the unity-2d and are forcing everyone on unity-3d which breaks on some type of graphics cards (graphics driver issues).

---

### Post by hunterkasy on 2012-11-28
I am wondering if this issue is fixed or not? I want to upgrade but don't want to fall into the mess again

---

### Post by pedro.nariyoshi on 2012-11-28
It should work on a clean install. As I've stated before, the problem is that fglrx has dropped support for our "legacy" devices.

You have to purge fglrx and install the radeon (free-source) driver. Check if "radeon" is blacklisted or fglrx is set to be "autoloaded".

If you don't know how to do these things, please copy this to us:
```
cat /var/log/Xorg.0.log | grep EE
```

This should help us help you (;

---

### Post by hunterkasy on 2012-11-28
> **pedro.nariyoshi said:**
> It should work on a clean install. As I've stated before, the problem is that fglrx has dropped support for our "legacy" devices.

You have to purge fglrx and install the radeon (free-source) driver. Check if "radeon" is blacklisted or fglrx is set to be "autoloaded".

If you don't know how to do these things, please copy this to us:
```
cat /var/log/Xorg.0.log | grep EE
```

This should help us help you (;

also how about upgrading from 12.04 to 12.10 should it also work?

laurie@laurie-Inspiron-537s:~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.431] (II) Loading extension MIT-SCREEN-SAVER
laurie@laurie-Inspiron-537s:~$

---

### Post by pedro.nariyoshi on 2012-11-28
As long as you are not using fglrx (closed) driver, it should work. You can do a```
sudo apt-get purge fglrx*

``` just to make sure

If you already upgraded, you can still fix it. One suggestion is to install the gnome-fallback or other DEs that don't require 3d acceleration, so you can have a "failsafe" option.

---

### Post by hunterkasy on 2012-11-28
> **pedro.nariyoshi said:**
> As long as you are not using fglrx (closed) driver, it should work. You can do a```
sudo apt-get purge fglrx*

``` just to make sure

If you already upgraded, you can still fix it. One suggestion is to install the gnome-fallback or other DEs that don't require 3d acceleration, so you can have a "failsafe" option.

I want to thank you my upgrade went good everything is happy so I am happy

---

### Post by pedro.nariyoshi on 2012-11-28
And we are happy too :D

---

### Post by Monotoko on 2012-11-28
oldfred, just wanted to jump in and thank you. I've been dealing with compiz crashing on my nVidia card for days now and it's drove me to the point of insanity.

---

### Post by hunterkasy on 2013-04-12
I have a intel quad core with 8gigs of memory
with a evga nvidia geforce 460 graphics card
just did a clean install of 12.10 everthing went well I updated the system and now the top panal and launcher is gone
can someone help me thanks

---

### Post by oldfred on 2013-04-12
Did you run the update commands in posts 3 & 4?
You have to install headers first then nVidia driver.

 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

