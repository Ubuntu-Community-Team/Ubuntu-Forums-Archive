---
title: "[SOLVED] Building from Ubuntu Source"
date: 2007-08-05
forum: General Help
---

### Post by Megaqwerty on 2007-08-05
Hi, I've been building packages using: ```
apt-get -b source
``` to make sure a few apps were built completely optimized for my box. 

This works beautifully. However, Update Manager is telling me I have updates for those apps after I install the locally built version. 

It's the same version of the software, just built locally, so it makes no sense to go back to what I was trying to avoid, just because it's built by my computer, not the Ubuntu maintainer's. 

It's a pain to have to uncheck them every time I want to upgrade, and even worse, I don't know if it's actually an update unless I check the version numbering on every updated package (once again, a pain.) Any idea how I can stop Ubuntu from doing this?

Thanks,

Megaqwerty

---

### Post by apswartz on 2007-08-05
Strange.

I don't have any idea. The only stuff I build from source is the stuff I can't get binaries for so there would be no conflict.

Hope you can figure it out. Good luck.

---

### Post by Megaqwerty on 2007-08-06
> **apswartz said:**
> Strange.

I don't have any idea. The only stuff I build from source is the stuff I can't get binaries for so there would be no conflict.

Hope you can figure it out. Good luck.

As it is with me and my incessant need to figure things out lest I suffer insomnia, I've figured out a simple solution thanks to my dabbling in debain package creation.

Here is how I did it for ffmpeg:

```
mkdir ~/Desktop/optimize
cd ~/Desktop/optimize
sudo apt-get build-dep ffmpeg
apt-get source ffmpeg
```
I then have the source code in my optimize directory. So, I then want to make sure it will not get replaced by the one currently in the Ubuntu repository. So I run: ```
cd ffmpeg-0.cvs20060823
dch
```
I then change it from this (truncated for brevity):
```
ffmpeg (3:0.cvs20060823-3.1ubuntu**4**) feisty; urgency=low
```
to this:
```
ffmpeg (3:0.cvs20060823-3.1ubuntu**5**) feisty; urgency=low
```
Save, close, and run these commands:
```
#iIt's fine if this ends with a debsign error
debuild -S
sudo dpkg-buildpackage
```
Or, if you don't want to run it as root, and you have fakeroot installed, you can run:
```
debuild -S
dpkg-buildpackage -rfakeroot
```

Since Ubuntu tells you that you need to upgrade when the same revision is installed, it will actually inform you when an update is available (this time, legitimately.) 

Hope that helps anyone else with this problem,

Megaqwerty

---

