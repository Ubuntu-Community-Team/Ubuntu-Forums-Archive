---
title: "Three monitors. Two light up mirrored."
date: 2017-01-31
forum: General Help
---

### Post by isignisign on 2017-01-31
I am unable to get all three of my monitors to show.
I can get two of them two of them to show but they simply mirror each other.
The left most monitor uses DVI - no shows
The center monitor also uses DVI - shows
The right most monitor uses HDMI - shows

I am using a Radeon R9 390 GPU
Ubuntu Version 16.04.1

The output of
```
xrandr
``` 

is 
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080     77.00*
```

---

### Post by QIII on 2017-01-31
Hello!

Which release of Ubuntu are you running?

---

### Post by isignisign on 2017-02-01
I edited the post with that new information
Ubuntu 16.04.1

---

### Post by QIII on 2017-02-01
Thanks!

Next question:  are you running the default open source driver, AMDGPU, or have you installed AMDGPU-PRO?

---

### Post by isignisign on 2017-02-01
So initially when I installed unbuntu the FPS was really low like 3FPS low I could literally see the frames replacing one another. So I downloaded AMDGPU-pro and restarted that got me into a login loop which I fixed by uninstalling it. The general consensus after searching the internet seems to be that happens when your GPU isnt supported by the driver but my R9 390 was on the list of supported cards which I found weird. So next I tried out Oibaf. Which I did
```
[COLOR=#333333][FONT=monospace]sudo add-apt-repository ppa:oibaf/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]graphics-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]drivers
[/FONT][/COLOR]sudo apt-get update
sudo apt-get upgrade
```

I've tried no other drivers so far.
This is where I currently am at.

I can see you're constructing help pages on AMDGPU and AMDGPU-PRO was there something that I could have done?

---

### Post by QIII on 2017-02-01
I'm not sure what oibaf has, whether or not just adding the PPA changes your driver or how to ensure that anything found there is working properly.

There are no guarantees with PPAs, so it's difficult to help with diagnosing problems.

I can tell you this:  AMDGPU-PRO was experimental for 16.04.  It works fine in 16.10 -- and is even in the repo.  I did get AMDGPU-PRO to work with my R9 380X by moving to a newer main-line kernel.

If you have a look at my blog, the latest article describes how I used the 4.8 kernel to get AMDGPU-PRO to work with 16.04.  Hopefully, a newer point release beyond 16.04.1 will include a kernel that works.

---

### Post by isignisign on 2017-02-01
I've a very basic understanding of computer systems so please forgive my next questions.

If I update my kernel to 16.10 there is a chance I can get AMDGPU-Pro to work?

If I update my kernel to 16.04.8 there is a smaller chance to get AMDGPU-Pro to work?

Thanks for the prompt replys and assisting me!

---

### Post by QIII on 2017-02-01
16.10 is a release of Ubuntu, not a kernel.  However, if you *install* 16.10, AMDGPU-PRO will likely work because it uses a kernel that is equipped to use AMDGPU-PRO.

16.04.8 would be a point release of Ubuntu 16.04 and is still not a kernel.  And that point release will likely never be released.  Maybe .5.

The kernel I used at the time I wrote that article was the main-line 4.8 Linux kernel.  Ubuntu is a Linux-based OS, but Ubuntu is not all there is to Linux.  Ubuntu is just one of many Linux distributions.

[This article]("https://www.linux.com/what-is-linux") might be enlightening.

---

### Post by isignisign on 2017-02-01
The article definitely clarified somethings for me. So taking your advice I installed 16.10. You did say that AMDGPU-PRO worked in this release and that it was even in the repo. Was it wrong to assume that once upgraded everything would just run?

right now on 16.10 The FPS is back to being very low (3FPS or something really low).

---

### Post by QIII on 2017-02-01
I don't know that 16.10 was my advice, exactly.  A suggestion.

Anyway, to get AMDGPU-PRO running, it has to be installed.  Right now you should be running AMDGPU by default.

I'm not terribly familiar with Unity's software tool, since I always install synaptic on any flavor I run.  But you should be able to search for AMDGPU-PRO.  Before you install, though, let us know what you find.

---

### Post by isignisign on 2017-02-01
I am not sure what you mean by search.
I did not find anything in the ubuntu software app
I did look at the software & updates

in additional drivers I have
[IMG]http://i.imgur.com/i6gwOGd.png[/IMG]

in other software I see
[IMG]http://i.imgur.com/bDnAhmj.png[/IMG]

---

### Post by QIII on 2017-02-01
Ah!  Had to check.  The R9 390 is a GCN 1.1 GPU.  The AMDGPU-PRO available at the 16.10 release date only works with GCN 1.2 GPUs (like mine) and later.  This is being extended back to GCN 1.0, but Ubuntu 16.10 won't consider your card able to use AMDGPU-PRO right now, so won't offer it as a driver option.

I can't vouch for the PPA you used, but if that was an improvement you can use that.

---

### Post by isignisign on 2017-02-01
so is there no way to enable multiple monitors? The PPA I was using didn't fix the problem.

---

### Post by QIII on 2017-02-01
I'll have to do a bit of research.

I'll need to know for sure which open source driver is currently in use.  We'll ask your machine to list the kernel modules loaded, filtered on two modules of interest.

First, please issue the following and post back the command and results:

```
lsmod | grep radeon
```

and then

```
lsmod | grep amdgpu
```

---

### Post by isignisign on 2017-02-01
I ran the two commands and neither showed anything

---

### Post by isignisign on 2017-02-02
So do you have any advice/next steps?

---

