---
title: "x60s Battery Life"
date: 2008-04-27
forum: General Help
---

### Post by MikeKnoop on 2008-04-27
I'm running Ubuntu 8.04 on my Lenovo x60s with an 8-cell battery.

I've done some research and found a bit of information on this subject, but none of which really added any significant lifespan to my 8-cell battery. I was pushing 7-8 hours under Vista and now in Ubuntu, I'm slightly pushing 4. 

Here's the interesting part. I'm dual booting both Vista and Ubuntu and when I booted back into Vista for the first time since installing Ubuntu, Vista is now reporting only about 4 hours of battery life!

I suspect that one of the tutorials I followed directly interfaced with the hardware somehow, as that's the only possible reason I can see the battery life being affected in both operating systems.

Any thoughts?

Thanks,
-Mike

---

### Post by syxbit on 2008-04-27
Ubuntu has always been much worse for battery life than Windows (despite what some people might say/hope)
it's an area where there really needs to be an improvement.
the drivers just aren't there.
my laptop gets 2h in Ubuntu, and a little over 3h in Windows.
I'd rather have 2h in linux than a million in windows, so it's an acceptable set back.

---

### Post by MikeKnoop on 2008-04-27
Yes, this is what I've gathered from reading other posts and whatnot.

But I'm more concerned as to why my Vista battery life has taken a hit after installing Ubuntu?

-Mike

---

### Post by syxbit on 2008-04-28
that shouldn't be possible.
the only thing i can think of is if you repartitioned your hard drive.
it's probably better to create partitions than to repartition.
this could cause your HD to be a little slower, and use more battery life, but i would imagine that difference to be ~1%

---

### Post by MikeKnoop on 2008-04-28
Hmm. Are you sure? I thought I read somewhere that battery time on the newer Lenovo laptop's is actually broadcast by the battery itself since it has hardware in the battery running firmware. I do know for sure they have some form of controller chip in the batteries - but to what extent it controls them I do not know.

-Mike

---

### Post by jeffeb3 on 2008-07-04
You've probably figured this out by now, but that 4 hours is an estimate.  Since you've been getting 4 hours in ubuntu, the battery thinks that's how long it will last.  When you boot into windows, the battery thinks, last time, I got 4 hours on one charge, this charge I'm probably going to get 4 hours.  But if vista sips the energy then it will still last 8 hours.  

BTW, did you have any installation issues with ubuntu?  have you found any neat tricks to improve the battery life?  I'm about to install on an older x60s that runs xp.

---

### Post by MikeKnoop on 2008-07-04
Yea, I finally think I realized that! In fact I did find a number of things to do in order to extend my battery life. I made a script which ran on bootup (put all the contents in my /etc/rc.local file.)

The commands I added were those suggested by powerTOP (search synaptic pkg mngr for it). That program is also really nice for monitoring battery life. As well as another one I found recommended online:

```

rmmod uhci_hcd

```

That disables the USB 1.1 ports on your laptop, which eat up a significant amount of battery, as well as makes the x60 run a lot hotter than need to. Note that you can reenable it with "modprobe uhci_mod" to reenable those USB ports. One last thing, I found a website detailing how to put the wireless card into low power mode, but it was only for the INTEL wireless card (I had the Atheros one). I did not save the website, but I found is either seraching for "x60s battery life" through google or through these forums.

Hope this helps!
-Mike

---

### Post by MikeKnoop on 2008-07-04
I've uploaded the file to my webserver:

[http://www.mikeknoop.com/upload/min_power_use.sh](http://www.mikeknoop.com/upload/min_power_use.sh)

Also, if you use the docking station with your x60s, you might be interested in this other glitch I ran across (as well as a fix):

[http://ubuntuforums.org/showthread.php?t=816755](http://ubuntuforums.org/showthread.php?t=816755)

-Mike

---

### Post by zee on 2008-10-21
Any difference in the overall temperature of the laptop and the battery time?

---

### Post by archer6 on 2008-11-18
I've installed Ubuntu 8.04.1 on my X60s, and I'm experiencing battery life that's quite similar to what I got when I was running XP Pro. Where temps are concerned it's the same as before, runs quite cool and quiet. Everything worked great after the install, and no tweaks were required. I'm completely satisfied with the outcome. Makes a great laptop. 

Cheers

---

### Post by zee on 2008-11-19
Thank you for the information.

---

