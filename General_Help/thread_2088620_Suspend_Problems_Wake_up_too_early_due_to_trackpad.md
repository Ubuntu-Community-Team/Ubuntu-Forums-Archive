---
title: "Suspend Problems Wake up too early due to trackpad"
date: 2012-11-27
forum: General Help
---

### Post by ziangpeterchen on 2012-11-27
Hello, 
1st post here.

Been googling around a lot and couldn't find anything to get this remedied. I had a problem with my chromebook 550 installed with chrubuntu 12.04 to stay standby with suspend. Then I did some poking and proding and finally figured out that the screen on the lid was causing capacitative movement on the trackpad thus waking it up. I did some further tests and confirmed that it was the cause.

I went for a solution to disable trackpad.

I used synaptic track pad disabling
touchpad indicator (defunct)
and finally xinput and then set enabled to 0 and finally was able to render the trackpad useless so I figured that was a good time to put it to suspend. 

I proceeded to touch the trackpad and then it woke up and the trackpad worked after being woken up without a restore function from xinput.

Now I'm stuck. I can't use a laptop that cant go standby and even though it boots in 2 seconds its annoying to shut off so I cant keep my files active. I'm looking for a solution to possibly get suspend to work and thus looking for ways to enable wake up such as pressing power is the only way to wake it up so track pad won't work. I'm having trouble finding solutions because when I google, I only get people having trouble with 12.04 from wake up getting into a black screen and I don't have that problem at all.

Thanks in advance

EDIT:

I can dual boot to chromeos and it has no problem staying in standby.

EDIT:

Fixed

[http://wiki.xbmc.org/index.php?title=How-to:Enable_Wake-On-Device_for_Ubuntu](http://wiki.xbmc.org/index.php?title=How-to:Enable_Wake-On-Device_for_Ubuntu)


Fix with Trouble shoot
Sudo su root

echo TPAD > /proc/acpi/wakeup

---

### Post by krustenBrot on 2012-11-27
Hey there,
you might want to take a look at 
> gedit /proc/acpi/wakeup
this is the list of wakeup devices and shows if they are enabled or not. But these are different from machine to machine. To find your touchpad you can try to identify it with looking at > lspci -v

---

### Post by ziangpeterchen on 2012-11-27
I can see the TPAD is enabled. when I go in to edit it, it wont let me save. Also ran it as sudo but didn't work.

EDIT: Problem Fixed

---

### Post by yochaigal on 2012-12-06
> **ziangpeterchen said:**
> Hello, 
1st post here.

Been googling around a lot and couldn't find anything to get this remedied. I had a problem with my chromebook 550 installed with chrubuntu 12.04 to stay standby with suspend. Then I did some poking and proding and finally figured out that the screen on the lid was causing capacitative movement on the trackpad thus waking it up. I did some further tests and confirmed that it was the cause.

I went for a solution to disable trackpad.

I used synaptic track pad disabling
touchpad indicator (defunct)
and finally xinput and then set enabled to 0 and finally was able to render the trackpad useless so I figured that was a good time to put it to suspend. 

I proceeded to touch the trackpad and then it woke up and the trackpad worked after being woken up without a restore function from xinput.

Now I'm stuck. I can't use a laptop that cant go standby and even though it boots in 2 seconds its annoying to shut off so I cant keep my files active. I'm looking for a solution to possibly get suspend to work and thus looking for ways to enable wake up such as pressing power is the only way to wake it up so track pad won't work. I'm having trouble finding solutions because when I google, I only get people having trouble with 12.04 from wake up getting into a black screen and I don't have that problem at all.

Thanks in advance

EDIT:

I can dual boot to chromeos and it has no problem staying in standby.

EDIT:

Fixed

[http://wiki.xbmc.org/index.php?title=How-to:Enable_Wake-On-Device_for_Ubuntu](http://wiki.xbmc.org/index.php?title=How-to:Enable_Wake-On-Device_for_Ubuntu)


Fix with Trouble shoot
Sudo su root

echo TPAD > /proc/acpi/wakeup


Thanks so much for this!  I've been looking around as well - google didn't return anything for "ubuntu chromebook suspend wakes randomly" or whatever I had typed.

---

### Post by yochaigal on 2012-12-17
Ok strange issue...

Now, Ubuntu on my Samsung S 550 Chromebook no longer wakes from suspends... if I close the lid or initiate pm-suspend manually the machine boots normally rather than waking up!

I know it is suspending properly as pm-suspend.log shows as much; nothing in syslog shows any problems either.

This leads me to think that the issue is NOT a failure but rather a configuration problem.  The weird thing is, I've wiped the filesystems and reinstalled ubuntu the same way as I did originally (see [here]("http://chromeos-cr48.blogspot.com/2012/04/chrubuntu-1204-now-with-double-bits.html?showComment=1337967575886#c7264339896129002789")) and the problem persists!  

I've tried adding various kernel options to my grub config (see [here]("http://ubuntuforums.org/showthread.php?t=1596545&page=6")) to no avail.

Since there is literally not a single post mentioning a successful chromebook install besides this one, I thought I'd post here!  Any help you offer is most appreciated.

Thanks

---

### Post by ziangpeterchen on 2013-01-14
@yochaigal

I've had the same problems that I have tried to fix. It might be a bios issue or compatability issue with chrome. To fix this...

I installed chromium os build from hexxeh [http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)

Then install process is here

[http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/samsung-sandy-bridge](http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/samsung-sandy-bridge)

hope that helps

---

### Post by yochaigal on 2013-01-15
Just so I understand:

You have a Samsung Series 5 550, and you had exactly that same suspend experience? And installing the hexxeh version fixed it?

---

### Post by yochaigal on 2013-01-16
Ok, I tried this and it worked!
Suspend worked in both ChromeOS and Ubuntu... my only issue is that I was unable to replace Ubuntu with Arch (as I had been able to before) by just dumping a rootfs - I'm guessing it's related to the kernel.
The hexxeh build is nice but doesn't have flash support unfortunately.

What I don't understand is: 
Why did suspend work on stock Chromeos+Ubuntu for a few weeks, then suddenly stop?

And why doesn't anyone else experience this issue (I haven't seen it mentioned ANYWHERE, excepting this thread)?

---

### Post by daboross on 2013-09-24
I have the same issue where the touchpad will wake the computer from suspend, however I upgraded to 13.04, and the /proc/acpi directory doesn't exist. I'm not sure how to fix this, as there is no /proc/acpi/wakeup file, or /proc/acpi directory.

---

### Post by yochaigal on 2013-09-24
> **daboross said:**
> I have the same issue where the touchpad will wake the computer from suspend, however I upgraded to 13.04, and the /proc/acpi directory doesn't exist. I'm not sure how to fix this, as there is no /proc/acpi/wakeup file, or /proc/acpi directory.

I am running 13.04 and I have /proc/acpi - are you sure it isn't there?
If you do ls -l /proc/acpi  what do you see?

---

### Post by daboross on 2013-09-24
> **yochaigal said:**
> I am running 13.04 and I have /proc/acpi - are you sure it isn't there?
If you do ls -l /proc/acpi  what do you see?

Here is the output of ls -l /proc and ls -l /proc/acpi: [http://sprunge.us/EiWD](http://sprunge.us/EiWD)

It just doesn't seem to be there.

---

### Post by yochaigal on 2013-09-24
Do you have acpi disabled in GRUB?  
As in, is there an acpi=off option in grub.cfg?

---

### Post by daboross on 2013-09-24
> **yochaigal said:**
> Do you have acpi disabled in GRUB?  
As in, is there an acpi=off option in grub.cfg?

I don't believe that grub is on this computer, there are no grub* packages installed and there is no /etc/default/grub. Where would I find grub.cfg if I did have it installed? I would only know where the 'grub' config is.

---

### Post by yochaigal on 2013-09-24
Oh, right we're talking about a chromebook, I forgot (I sold mine a few months back specifically because of kernel issues).
On my lenovo, which runs 13.04, I have /proc/acpi - so I can only assume that acpi was uninstalled/disabled.
The chromebook kernel is still built with acpi options - I built mine using [this]("https://groups.google.com/forum/#!topic/chromebook-central/PPQFpC7mYzk") guide.  It solved most of my issues (and I had acpi).

---

