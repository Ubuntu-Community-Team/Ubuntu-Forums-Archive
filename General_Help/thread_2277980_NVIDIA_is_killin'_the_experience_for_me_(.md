---
title: "NVIDIA is killin' the experience for me :("
date: 2015-05-13
forum: General Help
---

### Post by spasmoid on 2015-05-13
Certainly no fault of Ubuntu. I've been using Ubuntu on and off for a few years now. I am not a sys-admin type of person but I do have a Debian background and I'm willing to put some effort in to get stuff done but Oh My God this whole thing with NVIDIA is making it all too hard.

Every time I want to do a dist-upgrade, it breaks the NVIDIA driver config because it is tied to the kernel. So then you gotta go through the whole NVIDIA install routine again. I usually drag myself over to their website to manually download the binary file because it's all too hard for them to have an apt source. Then every single time there is some new random error that is has when trying to make it go. Doing "apt-get install kernel-sources" is not good enough, so you have to magically know all this stuff about backticks and uname-r to magically guess what you're supposed to feed apt-get just so that nvidia can find the sources. They wanna have their own binary, but their script can't automatically get the kernel sources.

This time I finally got it to go, and now X won't start. rebooting lands me at a text login screen and startx and X will just make the screen go black. I switch to another terminal and try and run it again but it is apparently running. Still the screen is not doing anything.

All I want is a linux box that drives my 4K display efficiently (with Kodi and occasional desktop web browsing) but cannot do this with the standard drivers that come with the distro. They don't cut the mustard for 4K video playback. So hence all the NVIDIA pain and suffering. This is like the 5th time I've had to mess about with NVIDIA install and every time the problem is different and it takes like a full day of my time. Very frustrating. This one issue alone will send me back to Windoze because it just works :(

---

### Post by oldos2er on 2015-05-13
I use the xorg-edgers PPA for drivers for my 750ti. You don't mention which card you have, so I'm unsure whether to recommend xorg-edgers or x-swat.

---

### Post by Aimeelin on 2015-05-13
A painful experience, but you use the NVidia hardware, you can get the drivers from [here]("https://www.driverdr.com/nvidia-drivers/").

---

