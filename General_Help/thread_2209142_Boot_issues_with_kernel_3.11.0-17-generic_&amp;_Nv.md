---
title: "Boot issues with kernel 3.11.0-17-generic &amp; Nvidia GeForce GTX 650 (propriety)"
date: 2014-03-04
forum: General Help
---

### Post by leo_mancini on 2014-03-04
Hi all, 

When using the latest available Kernel 3.11.0-17-generic combined with the Nvidia-319 (propriety, tested) drivers, I am unable to successfully boot into X - (or the system GUI). 

In order to successfully boot up I'm holding down the shift key on boot and selecting kernel 3.11.0-14-generic.

The issue appears to be that (according to my Xorg.1.log file) that >  [  1839.127] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[  1839.127] (EE) NVIDIA:     system's kernel log for additional error messages. 

An example of my Xorg.1.log file is on the following link
[http://paste.ubuntu.com/7032308/](http://paste.ubuntu.com/7032308/)

Please advise if you require more information.

I would like to know options of what I can do to either boot into my desktop with the latest kernel version. Upgrade to a later Nvidia driver or anything else suggested.

Thank you.

---

### Post by phidia on 2014-03-04
It sounds like you might have a kernel-driver mismatch. In other words with a custom driver you need to build that driver each time the kernel is updated, or that's how things used to work.

You can open a terminal and plug this in: # dpkg-reconfigure nvidia-kernel-dkms
 See what output you get.

---

### Post by leo_mancini on 2014-03-05
I receive an error message dpkg-query:package 'nvidia- kernel-dkms' is not installed and no information is available

---

### Post by oldfred on 2014-03-06
Did you install nVidia from Ubuntu repository or a ppa or nVidia directly?

Best to only install from Ubuntu as the others require lots of effort to continue to keep working.
And once you install from one source you have to totally purge all nVidia and xorg and reinstall from scratch. Otherwise you get major conflicts.

---

### Post by leo_mancini on 2014-03-07
Hi there,

I ended up resolving this myself.
Please note - I did not have any third party ppa's installed.
I had the nvidia-319 (propriety, tested) drivers installed - which led to the blank screen.

Surprisingly now that I have changed the driver to the nvidia-319 (Propriety)  - this does not result in a blank screen when loading Ubuntu.

Working fantastically.

 :guitar:

---

