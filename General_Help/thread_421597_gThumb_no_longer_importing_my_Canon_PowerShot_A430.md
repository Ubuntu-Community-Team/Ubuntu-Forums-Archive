---
title: "gThumb no longer importing my Canon PowerShot A430's images under Feisty"
date: 2007-04-24
forum: General Help
---

### Post by MysticAurora on 2007-04-24
Hi. Just before I upgraded to Feisty -- from edgy -- I was able to use gThumb and import the pictures from my digital camera, which is a PowerShot A430. The last time I had the problem in edgy, I was referred to a few bug reports where the solution was unclear and nothing I tried worked. I just searched the forums and it seems like there might be a backport solution. I've enabled feisty-backports, yet I still don't see any different gThumb or gphoto versions.

I'm using the following with an up-to-date install of feisty:

gthumb 3:2.10.2
gphoto2 2.2.0-3
libgphoto2-2 2.3.0-0

Are there any fixes out there that will actually work? 'lsusb' gives me the following output related to the camera:
```

Bus 002 Device 012: ID 04a9:30f8 Canon, Inc.

```

gThumb even asks me if I want to import photos when it detects my camera. When I tell it to go ahead; it then gets stuck on searching for drivers and I end up having to force-kill it.

---

### Post by Billy McCann on 2007-04-25
I'm getting the same sort of problems.  But mine worked under Feisty like two days ago and now it seems to not be able to find the driver.  

It's a bummer too because I asked folks for help selecting a camera that would work fine with Ubuntu.  :(

---

### Post by Billy McCann on 2007-04-25
Mystic Aurora,

I was able to solve my camera's problem.  Read my thread.  

[http://ubuntuforums.org/showthread.php?p=2532573](http://ubuntuforums.org/showthread.php?p=2532573)

Mine acts a little weird, but it works.  :KS

---

### Post by MysticAurora on 2007-04-27
> **Billy McCann said:**
> Mystic Aurora,

I was able to solve my camera's problem.  Read my thread.  

[http://ubuntuforums.org/showthread.php?p=2532573](http://ubuntuforums.org/showthread.php?p=2532573)

Mine acts a little weird, but it works.  :KS

I tried that out and had to replace SUBSYSTEM! with BUS!, but I still get an error with i/o claiming. It says it can't claim the device. I checked the rules file against 'lsusb' and my camera's listed there. I don't understand what the problem is.

---

### Post by Gotty on 2007-04-27
I have the same problem, with the same camera. I've tried all sorts of libgphoto2 modifications, but I always get an error. With the usb_device trick, I get "Permission denied on USB device" (or something like that, I have it in French). And if I try a sudo gthumb, it freezes for 5 minutes before giving  a "PTP error"...

EDIT : I have to add that I do not have the problem with my Nikon D70 (which is not in PTP)

---

### Post by HyperY2K on 2007-04-30
After upgrading to feisty fawn I've got the same errors with my Canon EOS 350D.
Is there any possibility to use all gphoto versions under feisty?

---

### Post by sameat on 2007-04-30
Same Camera, Same issue (running feisty).  I've tried all of the fixes in this forum to no avail.  Has anybody found an alternative solution?

Thanks,

---

### Post by Billy McCann on 2007-05-01
Do you get TWO "Camera detected" notifications?  don't touch the first one. Wait for a second one.  IF the second one appears, it'll work.

---

### Post by HyperY2K on 2007-05-01
no I only get one camera...

---

### Post by Amphios on 2007-05-01
Same problem here ... None of the work-arounds seem to help. Is there a bug report at launchpad? With Edgy, my Canon A430 worked just fine.

I also get only one notification. :(

---

### Post by sameat on 2007-05-01
Does this look relevant?

[http://www.nabble.com/Problems-using-gphoto2-connected-through-USB-with-Canon-Powershot-A430.-tf3596630.html#a10148014](http://www.nabble.com/Problems-using-gphoto2-connected-through-USB-with-Canon-Powershot-A430.-tf3596630.html#a10148014)

Downgrading libgphoto finally solved the problem for me (I can connect to and download form my canon a430 in feisty).  Now I am going to see if there is a way to get it upgraded past the bad version.

---

### Post by MysticAurora on 2007-05-01
> **sameat said:**
> Does this look relevant?

[http://www.nabble.com/Problems-using-gphoto2-connected-through-USB-with-Canon-Powershot-A430.-tf3596630.html#a10148014](http://www.nabble.com/Problems-using-gphoto2-connected-through-USB-with-Canon-Powershot-A430.-tf3596630.html#a10148014)

Downgrading libgphoto finally solved the problem for me (I can connect to and download form my canon a430 in feisty).  Now I am going to see if there is a way to get it upgraded past the bad version.

How did you downgrade libgphoto? I searched for "gphoto" in Synaptic and each relevant package only has one version. I'm unable to downgrade. :\

---

### Post by HyperY2K on 2007-05-02
> **MysticAurora said:**
> How did you downgrade libgphoto? I searched for "gphoto" in Synaptic and each relevant package only has one version. I'm unable to downgrade. :\

for me too. How can I downgrade gphoto in Feisty Fawn?

---

### Post by sameat on 2007-05-02
I'll tell you how I did it, but it doesn't seem like the correct way to me...please don't think of this as advice.

1.  Remove libgphoto2-2 and libgphoto2-port0.  A few other packages will go away because of dependencies, so pay attention to what you are losing...this wasn't a deal breaker for me but it might be for you.

2.  Switch repos to edgy (edit sources.list)

3.  Install edgy version of libgphoto2-2 and the frontend you want (I use gtkam). 

4. Switch repos back.

I can do step by step instructions if they are needed...never sure about the level of expertise in forums.

Obviously, this isn't a long term solution...I mostly did it to see if there was actually a bug (and there is, so one of us should report it, but I can't produce meaningful debugging info at the moment since mine is working).  

Running updates will break this again until it is fixed.  I made sure I was up to date before I started all of this.  I looked in to pinning those packages, but I'm not that worried about updates until this is fixed  so I dropped it.

Good Luck

---

### Post by psycosmyth on 2007-05-05
OK this is weird!
I just reverted TO edgy all the way and now my Powershot A85 is not being permitted to be read, same issue with you guys in fiesty. AHHHHHHHHHhh:( 
I have tried everything I know.

---

### Post by lorenzo_de_tomasi on 2007-05-11
Same problem: PTP I/O Error with Canon Powershot A430 :-(
Followed a lot of threads, but no solution found...

Thank you

---

### Post by Keith_Beef on 2007-05-12
My Canon PowerShot A610 no longer works. :(

It was fine in 6.06, but since 7.04 I get this message:

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Any idea what this could be, or even *which* I/O library is causing the problem?


Beef.

---

### Post by hob4bit on 2007-05-13
Hi, I have a Sony Cybershot camera which works using the PTP interface
in Ubuntu-6.10 using gthumb. It does not work with same procedure under Ubuntu-7.04.

I searched everywhere for a fix. Then found this downgrade method. I personally use my own written scripts to deal with working out dependencies and upgrades.

The following will fix all "gthumb" problems  in Ubuntu-7.04 where it used to work in Ubuntu-6.10:

wget [http://uk.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.2.1-2ubuntu4_i386.deb](http://uk.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.2.1-2ubuntu4_i386.deb)
wget [http://uk.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.2.1-2ubuntu4_i386.deb](http://uk.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.2.1-2ubuntu4_i386.deb)
wget [http://uk.archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.7.9-0ubuntu1_i386.deb](http://uk.archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.7.9-0ubuntu1_i386.deb)
dpkg -P f-spot
dpkg -i libgphoto2-port0_2.2.1-2ubuntu4_i386.deb libgphoto2-2_2.2.1-2ubuntu4_i386.deb gthumb_2.7.9-0ubuntu1_i386.deb

As a number of people have said its to do with a bug in "ibgphoto2" libraries. I don't use "f-spot" and this simplifies the dependencies by removing it. If you perform an update just re-issue the commands:

pkg -i libgphoto2-port0_2.2.1-2ubuntu4_i386.deb libgphoto2-2_2.2.1-2ubuntu4_i386.deb gthumb_2.7.9-0ubuntu1_i386.deb

You will need to store these three "deb" files until there is a proper fix for libgphoto 2.3 bugs.

This fixed my problems and I am once again happy with Ubuntu. I am surprised that Ubuntu has no official fix or workaround for this serious "libgphoto" bug. At least Ubuntu has good community forums for help.

Personally, I never upgrade my Linux installation. I have three Linux partitions:

hda6) Old stable = Ubuntu 6.06
hda7) Stable = Ubuntu 6.10
hda8) Testing = Ubuntu 7.0.4

Now I can use Ubuntu 7.04 as stable:

hda6) Unstable = Ubuntu latest
hda7) Old Stable = Ubuntu 6.10
hda8) Stable = Ubuntu 7.0.4

Hope this procedure for fixing "gthumb" is simpler than messy around with "sources.list".

---

### Post by Keith_Beef on 2007-05-13
Thanks, hob4bit. 

That worked a treat!


Beef

---

### Post by MysticAurora on 2007-05-14
hob4bit: Thanks SO much for the fix! It may be temporary, but I can finally get the images from my camera now!

If you guys don't want to hold onto the .deb files, you can find the packages in Synaptic, and go to Package -> Lock Version. However, you'll have to remember to unlock the version when a dependable upgrade for the three packages is available. I'm amazed at how many people this affected, though. Most upgrades in Ubuntu/Linux in general are beneficial and are improvements. Gthumb and so on ended up broken, pretty much. :(

---

### Post by Jimmy_r on 2007-07-06
So far I have not noticed that this has been fixed in feisty. I used to downgrade libgphoto to edgy version, but this got annoying fast as it prevented some apps including wine(?!) to be upgraded to latest versions.

A few days ago I tried Gutsy and saw it was fixed there, so I made a private backport of libgphoto from Gutsy.

Edit: Since Gutsy is now released, I have removed the debs and the link. I recommend upgrading to Gutsy, where this problem is fixed.

---

### Post by HyperY2K on 2007-08-12
is there any fix out there form Canonical?

---

