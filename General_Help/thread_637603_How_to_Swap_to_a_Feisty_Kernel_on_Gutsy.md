---
title: "How to Swap to a Feisty Kernel on Gutsy"
date: 2007-12-11
forum: General Help
---

### Post by IanLowe on 2007-12-11
Okay...

I'm having the Vmware Server issues (poor performance, high iowait and so on) that people seem to be reporting on the 2.6.22 Kernel.

I would like to at least try running on the Feisty Kernel, as several people are reporting much better results on that Kernel.

I have a 7.04 64 bit Server CD, which I would like to use as a source for apt-get (just as the 7.10 CD that I installed from is listed as a source), so that I can install the appropriate image.

I'm a little outside of my comfort zone on this one and coming up blank on my research, so would appreciate someone laying out the steps - how do I add a CD as a source for apt-get? is thaat an OK way to install another Kernel? (I want both to be available to boot from, rather than just the old one, as this is for testing purposes)

are there any big nasty gotchas about stepping back to the Feisty Kernel?

---

### Post by jamescondron on 2007-12-11
Personally, I'd try through GRUB. Hit escape as you boot up to get to the grub menu, select the kernel that way

---

### Post by IanLowe on 2007-12-11
Ah , sorry - this was a fresh installation of Gutsy, not an upgrade.

There isn't a Feisty Kernel on the machine - that's my question, how do I install one?

---

### Post by SeanHodges on 2007-12-11
I think the safest way will be to compile it from source.

Download the kernel source and Ubuntu patches from:

[http://packages.ubuntu.com/feisty/base/linux-image-2.6.20-15-386](http://packages.ubuntu.com/feisty/base/linux-image-2.6.20-15-386)

Apply the patches, and compile the kernel using the usual approach (search the wiki for this).

I haven't tried this, and it might be straight-forward or difficult. I'm not sure. It will definitely be the safest method as it will compile against Gutsy's core, and if theres something missing/wrongly configured you will most likely find out before you attempt to run it.


Regards,

Sean

---

### Post by SeanHodges on 2007-12-11
I might be wrong on this, but I don't think the install CD holds the source code for the packages it contains, you'll need to download the source from the packages site.

---

### Post by skymera on 2007-12-11
try

[www.kernel.org](www.kernel.org)

and perhaps compile an eearlier one.

---

### Post by oscarsfriend on 2007-12-11
There is a thread detailing how to install the Gutsy kernel (and only the kernel) from the repos on Feisty: [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

This method (the manual one) could surely be adapted to do the opposite.  Please note that I have not tried this, so I don't know what it might do (be sure to back up your Gutsy kernel and /boot/grub/menu.lst just in case).

---

### Post by IanLowe on 2007-12-11
Thanks oscarsfriend, that was exactly what I was looking for - I should be able to figure that out and give it a go this evening.

As for compiling from source, I can see what you are saying Sean, but I'm a little concerned that I would introduce some new factor into the vmware situation.

---

