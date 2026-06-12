---
title: "ATI X800XL problem (AMD64)"
date: 2006-07-06
forum: General Help
---

### Post by ashughes on 2006-07-06
Having just finished installing the latest ATI driver, I am getting the following error when trying to run aticonfig:

aticonfig: error while loading shared libraries: libfglrx_pp.so.1.0: cannot open shared object file: No such file or directory

I also get a similar error when trying to run fglrxinfo:

fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Now I assume this is because I am missing that lib file. But that begs the question, what other files might I be missing. Which makes me think that there is a "package" that contains that file that I am missing.

On a side note, before even attempting the ATI driver install (from ATI's website), I did the following:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx

Upon reconfiguring xorg.conf, I cannot get into X unless I revert back to the vesa drivers.

Also, I have checked through the list of installed packages in Synaptic, and from what I can see, I have all the required packages installed (no dev packages are installed)

Any suggestions??

---

