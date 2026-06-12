---
title: "same image different hardware"
date: 2013-02-13
forum: General Help
---

### Post by ScratchFive on 2013-02-13
hi all,

I'm thinking about moving an ssd (with a working ubuntu filesystem on it) to another machine, should I expect it to work and re-optimise itself for the new hardware? (more or less cores/ram, different GPU etc). I remember doing this with arch once and the shtf but knowing (a little) more about linux now that may well have been my fault.

thanks guys

---

### Post by matt_symes on 2013-02-13
Hi
 
you may have to install new wireless and graphics drivers, but apart from that, most other things should work.
 
You may want to post a list of both machines hardware so people can take a look.
 
Kind regards

---

### Post by ScratchFive on 2013-02-13
thanks, 

I don't have any fancy wireless cards or external GPUs so I'm thinking it should be fine

thanks again

---

### Post by |{urse on 2013-02-13
I love that about linux, you can install it, move the hard drive to a totally new hardware environment and 90% of the time it will work.

---

### Post by grahammechanical on 2013-02-13
At the first boot I would boot into Recovery Mode>Resume. That should load the desktop without activating the video driver. You can then log out and log back in to activate the video driver. If the desktop breaks then at least you know you can get to a desktop and change the video drvier through Additional Drivers. Depending on your video card you might want to try Nouveau (it is the default driver) as you experiment with video drivers.

Oh, one more thing. Plan a fresh install because during the install the OS will be set up with modules suitable for that particular set of hardware. 

Regards.

---

### Post by Rebelli0us on 2013-02-13
Everything should work, Linux is very portable. If you're using a proprietary video driver, I'd switch to generic/open source before moving.

---

### Post by matt_symes on 2013-02-13
Hi

Ubuntu should be able to load most of the kernel drivers as it discovers the hardware. 

You will still have onboard graphics so you may want to check out the driver required for the new video card.

If you have any problems then post here and we can help. 

If you have any special kernel parameters the remove them. Disable any special tweaking you may have done for specific hardware. You can always put them back later.

Ubuntu comes with a whole bunch of kernel modules when you install it. Some consider this bloat but it does provide flexibility.
```

matthew-S206:/home/matthew % modprobe -l | grep drivers | wc -l
2853
matthew-S206:/home/matthew %
```Kind regards

---

