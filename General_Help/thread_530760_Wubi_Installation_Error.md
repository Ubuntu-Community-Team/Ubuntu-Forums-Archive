---
title: "Wubi Installation Error"
date: 2007-08-20
forum: General Help
---

### Post by JJM02351 on 2007-08-20
I am attempting to install Xubuntu with Wubi on an old laptop with only a 6 GB harddrive and no bootable CD (Toshiba Portege 3110 CT, 128MB RAM max).  Win 98 is installed, and I was able to free 5+GB of space before starting Wubi.  Wubi told me to place a copy of the Xubuntu ISO file in /wubi/install, which I did (it passed the MD5 hash test).  I then had 4.37 GB of free space remaining.  I restarted Wubi and it errored, telling me that I had to have at least 4GB of space available, which I do.  

Has anyone else seen this error?  Is it a bug?

---

### Post by ago on 2007-08-21
It's in fact 5GB, considering the disk image to be downloaded, but wubi does not "discount" the space of an image already downloaded. So if you download an image is actually 5.7GB

---

### Post by JJM02351 on 2007-08-21
Thanks for the prompt reply.  I may have to use a smaller distro, like Puppy Linux, on this machine.

---

### Post by ago on 2007-08-21
It's not really that 4GB are strictly required, only a fraction is actually used in a default installation, but if we had the minimum to 2-3GB then lots of people would run out of space when installing extra software and we would have lots of support requests.

---

### Post by JJM02351 on 2007-08-21
I hear you...

Since I'm installing the alternative Xubuntu, I probably am at the low end of the space requirements.  Perhaps when the wubi functionality is incorporated into the main distro, there will be more flexibility.  

The work of all the independent and largely unpaid programmers is much appreciated.

---

### Post by samusz on 2007-08-21
Hi 

You could try out a net install with [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) They specify the following :
> Requirements
  [LIST]
[*]Linux, or Microsoft Windows 95-XP (Vista support is in the works)
[*]A broadband internet connection (dial-up will take way too long to download)
[*]3GB or more of spare hard drive space to install Ubuntu in[/LIST]   [B]
[/B]

Hope it helps ..

---

