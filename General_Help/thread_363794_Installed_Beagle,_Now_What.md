---
title: "Installed Beagle, Now What?"
date: 2007-02-17
forum: General Help
---

### Post by teejay17 on 2007-02-17
Okay, I downloaded and installed Beagle via Synaptic, as well as the other packages that come with it. Now what? I don't see it anywhere in the Applications, nor do I get it when I type "beagle" in the terminal. 
I've restarted, thinking that this programme would somehow get a jump-start after the reboot, but to no avail. 
There must be an easy way to get this feature working?

---

### Post by Shay Stephens on 2007-02-17
You need to run the daemon.  From the teminal run:
```
beagled
```

Then you should get an icon.  If not, create a launcher, and make the command:
```
beagle-search
```

I have been using it for a few days and really like it.  It will take a while for beagled to index everything, so be patient :-)

---

### Post by teejay17 on 2007-02-17
> **Shay Stephens said:**
> You need to run the daemon.  From the teminal run:
```
beagled
```Then you should get an icon.  If not, create a launcher, and make the command:
```
beagle-search
```I have been using it for a few days and really like it.  It will take a while for beagled to index everything, so be patient :-)
Okay thanks. I'm going to give this a try. I'll let you know how everything turns out. 
Cheers.

---

### Post by teejay17 on 2007-02-17
That didn't seem to work. Is it perhaps because my system is a little low on resources and Beagle is just not getting activated or something?

---

### Post by Maestro23 on 2007-02-17
> **teejay17 said:**
> That didn't seem to work. Is it perhaps because my system is a little low on resources and Beagle is just not getting activated or something?

I have read that Beagle is a resource hog.  What are you system specs?

---

### Post by teejay17 on 2007-02-17
> **Maestro23 said:**
> I have read that Beagle is a resource hog.  What are you system specs?
I'm ashamed to say that this old laptop that I use has 96 megs of RAM, and a Celeron Processor around the 700mhz range. If Beagle is such a resource hog, I bet it's not even getting activated, or not working properly, because of my system specs.

---

### Post by Shay Stephens on 2007-02-17
Reboot?

And don't worry about what computer you use.  If it works, more power to ya :-)

And the resources beagle uses is all up front as it indexes your drive(s).  Once that is done, it does indexing as things change, so the impact is very little once the main index is made.

---

### Post by kelbizzle on 2007-02-17
You can see exactly what beagle is doing. 
```
beagle-status
```
or
```
beagle-index-info
```

There is also a log located 
```
/home/YOUR_USERNAME/.beagle/Log/current-Beagle
```

If you want to make it index at full throttle (note this will really increase beagles priority) 
```
 beagle-shutdown
 export BEAGLE_EXERCISE_THE_DOG=1
 beagled
```

---

### Post by theDentist on 2007-02-18
He's right, I couldn't see it anywhere also so I thought like Windows (Oh Dear sorry folks!). Just REBOOT!.  Select PLACES, and then SEARCH there it is!

---

