---
title: "Broken Keyboard Shorts &amp; Fan Control - How to fix?"
date: 2019-02-14
forum: General Help
---

### Post by piggiesgosqueal on 2019-02-14
Okay, so I finished getting dual boot to work on my laptop.  I'm using Windows 10 and Ubuntu 18.04. My keyboard shortcuts work on Win  10 but not Ubuntu. I mainly want my fan control shortcut, screen  brightness, and keyboard brightness keyboard controls to work. With  Windows 10 I can use:
- FN + F5 for fan control
- FN + F7 & F8 for screen brightness
- FN + Up Arrow & Down Arrow for keyboard brightness

How can I set these to work in Ubuntu?

[LEFT]Here are my specs:[/LEFT]


[LIST=|INDENT=1]
[*]Computer: i7-8750H CPU @ 2.20   GHz - 32 GB RAM, 500 GB SSD & 1 TB HDD. I think my laptop has a   NVIDIA graphics card but idk what it is.
[*]Windows 10 Home 64-bit, 1803 version
[*]Bios: Asus Republic of Gamers (R.O.G.) BIOS v306 (Not 100% sure if it's just called that or if there's more..)
[*]Ubuntu Version: ubuntu-18.04.1-desktop-amd64
[/LIST]


ALSO, I'm trying to get my fans to change speeds once my laptop reaches certain temperatures. I've gone through 2 or 3 tutorials but keep having errors. The most recent one was related to not being able to find fan modules or something... I can check the exact error if needed. So far I've installed xsensors and can view the temperatures but not have the fan speeds change based off the temperatures.

Help would be greatly appreciated. Thanks!

Note: My laptop gets pretty hot when I'm on Ubuntu for a long time.

---

### Post by dragonfly41 on 2019-02-14
GKrellM is a useful utility for monitoring and I see that in Configuration it has fan control (processor and motherboard).
There is a range of optional plugins you can see if you search GKrellM in Synaptic Package Manager. The other sister package is GKrellMD.

---

### Post by piggiesgosqueal on 2019-02-15
@dragonfly41
Okay, I've installed GKrellM, how can I set it up to have fans work at a certain temperature? I've checked multiple sites but none of them provide instructions for it. Just the install command (which I've done).

I installed it using:
sudo apt-get update
sudo apt-get install gkrellm

I also did the commands here: [http://zoomadmin.com/HowToInstall/UbuntuPackage/gkrellm](http://zoomadmin.com/HowToInstall/UbuntuPackage/gkrellm)

---

### Post by dragonfly41 on 2019-02-15
I have not played with fancontrol but in gkrellm you can go to Configuration > Builtins > Sensors > Fans

click on Alerts

and you can launch a fancontrol command on any level (such as temp) being reached.

Each Alert trigger can run a command and now refer here for fancontrol commands.

[http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/](http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/)

and a more up to date link ..

[https://www.howtoinstall.co/en/ubuntu/xenial/fancontrol](https://www.howtoinstall.co/en/ubuntu/xenial/fancontrol)

---

