---
title: "Cant find kernel source"
date: 2007-02-28
forum: General Help
---

### Post by Blindraven on 2007-02-28
Ok, So I installed efty edge and had to install the Attansic gigbyte L1 drivers etc which was a pain in the ***, though - It never seemed to install correctly, it just worked somehow after i typed in make then modprobe atl1.

So i went STRAIGHT for automatix, downloaded the nvidia drivers and a few other things through it and decided i was sick of waiting so canceled what it was doing (half way through java i beleive)

Don't think this system like it much, when I rebooted to apply the nvidia stuff (which worked) it was off the net again, so i tryed reinstalling the lan drivers and it tells me it can not find the kernel source or some such crap.

I rebooted again to see what the "generic kernel" option did, and voila, somehow it booted up the normal version of ubunt and here I am.., but its not broken?

This does not satisfy me though, I want the normal option/ubuntu repaired.

Any help would be much appreciated.

T.

---

### Post by jocko on 2007-02-28
I'm not sure you need the complete kernel source, usually it works fine with kernel headers instead. To get them, find and install "linux-headers-generic" through synaptic, or type the following command in a terminal:```

sudo aptitude install linux-headers-generic
```Also I'm not sure what you mean by the "normal" vs. the "generic" ubuntu boot options.
Do you mean that you have both a -386 and -generic kernel installed? If that's the case, I think you have misunderstood something.
The -386 kernel is mainly for very old computers (older than the first pentium or pentium II processors, if I'm not mistaken).
The -generic kernel is optimised for modern processors and have support for some functions that the -386 kernels do not support (such as dual core or multiple processors).

If you by some reason still need to run a -386 kernel, you'll probably need kernel-headers-386 instead of linux-headers-generic.

Otherwise, search the forums for how to set a different default boot option and set it to boot the generic option, or simply uninstall the -386 kernel.

---

### Post by Blindraven on 2007-02-28
Its just a clean install, I did not user any extra paremetres, I wouldent know how to set them.

My boot screen looks "something"(but not exactly) like

Ubuntu (kernel version)
Ubuntu (restore mode)
Ubuntu ()failsafe)
Ubuntu (generic)
Ubuntu *(memtest)
Windows 1
Windows 2

I'd reboot now but i am installing media codecs and i dont want to cancel it unless it does what it did last time .

So does it sound like its installed the 386?
Does it normally do this default?

I'm running an M2V mobo with 7600gt, 1 gig DDR2 ram and an AM2  4200 duel core if that helps.

---

### Post by jocko on 2007-02-28
To see which kernel you are running, run this command in a terminal:
```
uname -r
```To see which kernels are installed, do a search for "linux-image" in synaptic, and see which "linux-image-*version_number*-*kernel_flavour*" packages are installed.

If you decide to remove an installed kernel, make sure you run the one you want to keep, and test that you get everything to work (I think some people have had problems with getting nvidia graphics drivers working on the -generic kernel, and that some version of nvidias drivers (or was it automatix or envy?) actually installed a -386 kernel, but hopefully that was only a temporary problem...)

[COLOR=Red]Edit:[/COLOR] I see you are using a dual core processor, then you definitely want to run the -generic kernel (I think the -386 kernel will only use one core).

---

### Post by Blindraven on 2007-02-28
Ok, 2.6.17-10-generic is what I am running on.

So I gues whatever else it was that I was running (being the first and default option) was wrong.

One other quick question,
I've gone ahead and ruined a few things up while they were downloading again..  is there a way to auto search for broken files so i can delete/update them?

From years ago i can vagually recall typing in dpkg grep | something or other.

Edit":

Yep, it seems there was a 386 version installed so I just removed it through synaptic.

---

### Post by jocko on 2007-02-28
synaptic should list any broken packages with the "broken" filter.
Otherwise read the help for dpkg, aptitude or apt-get ```
man dpkg
``` ```
man aptitude
``` ```
man apt-get
```

Good luck

---

