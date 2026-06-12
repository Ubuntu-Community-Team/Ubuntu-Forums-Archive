---
title: "apt-get update &amp; apt-get dist-upgrade do not get me the latest kernel, why?"
date: 2014-03-22
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-03-22
I've been thinking that```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```would get every update there was to get. I realise the middle one is redundant, lets ignore that. But apparently, while it will fetch new kernels and corresponding associated files, it does NOT necessarily fetch the newest kernel in the repository whenever there is something newer to fetch. Because I ran them and they didn't show anything as held back. Then I ran```
sudo apt-get install linux-generic
``` afterwards (following some directions slavishly) and it pulled down a new kernel and associated files. 

So why is that? Why didn't dist-upgrade get them to begin with? Or at least indicate the kernel was being held back?

linux-generic is a metapackage dependent on the latest versions of the kernel and its headers, and I believe the kernel-extras also. So now that I've installed it, I'd assume that NOW dist-upgrade will always get the latest kernel. Have I got that right?

It seems like a stupid "of course" question but that fact it isn't the default behaviour surprised me greatly. Are there any other update surprises out there I wouldn't suspect? Any other packages dist-upgrade will ignore unless I install a metapackage that demands the latest version?

---

### Post by coldcritter64 on 2014-03-22
> **Dreamer Fithp Apprentice said:**
> ..linux-generic is a metapackage dependent on the latest versions of the kernel and its headers, and I believe the kernel-extras also. So now that I've installed it, I'd assume that NOW dist-upgrade will always get the latest kernel. Have I got that right?...

Until the metapackage is installed you only get the originally installed kernel; _*though I thought that linux-generic being installed was the default with ubuntu*_, it surprised me a bit when you said you had to add it.

It is easy to inadvertently remove metapackages when installing/removing software, or maybe an install problem originally had it left out... just guessing there really.

Yes, dist-upgrade will keep you up with the latest released kernel for your release WITH the linux-generic package installed.

---

### Post by Dreamer Fithp Apprentice on 2014-03-22
Thanks, Coldcritter. I'm still trying to track down why it wasn't there. I'll post what I find out for the benefit of anyone who finds this thread because they were searching for info on a similar issue. I'm still wondering if there are any other packages apt-get dist-upgrade holds back while misleadingly reporting "0 held back" in the absence of a meta-package telling it "when I say "dist-upgrade" I mean, like, you know, upgrade. And at least admit it if you don't." Or can I be confident that this is the only package so misleadingly treated? So I'm going to hold off a bit on marking this solved.

---

### Post by coldcritter64 on 2014-03-22
> **Dreamer Fithp Apprentice said:**
> Thanks, Coldcritter. I'm still trying to track down why it wasn't there. I'll post what I find out for the benefit of anyone who finds this thread because they were searching for info on a similar issue. I'm still wondering if there are any other packages apt-get dist-upgrade holds back while misleadingly reporting "0 held back" in the absence of a meta-package telling it "when I say "dist-upgrade" I mean, like, you know, upgrade. And at least admit it if you don't." Or can I be confident that this is the only package so misleadingly treated? So I'm going to hold off a bit on marking this solved.

You can use the synaptic package manager and do a search for "meta-package". Most of the metapackages I've seen in synaptic [noparse](you will need to install it on newer Ubuntu releases : sudo apt-get install synaptic :)[/noparse] [s]are for kernel and hardware related stuff, specialist packages that you may not want automatically altered with an install[/s] **Edit: Ubuntu uses many more than I 1st thought, checked after a reboot into Ubuntu - ignore the stuck out comments, they are wrong in Ubuntu by a fair degree**. By installing the metapackage you then specifically tell the installation to keep  you up to date etc with commands like apt-get with the dist-upgrade option. I should note I checked with synaptic on Debian so Ubuntu may vary w.r.t. the use of metapackages.

Edit cont. :   a lot of meta packages in Ubuntu are being used to bring in dependencies for DEs and such as well it seems.

Still can only guess at why yours was missing. :)

---

