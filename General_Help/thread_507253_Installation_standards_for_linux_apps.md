---
title: "Installation standards for linux apps"
date: 2007-07-22
forum: General Help
---

### Post by Doughy on 2007-07-22
I am relatively new to linux (ubuntu) and I have spent the last few months getting up to speed on how to use it.  I am really enjoying the power of linux and all of the free software that is available.  I consider myself converted to linux.

One thing that I feel needs improvement, however, is the lack of a standardized installation mechanism.  There's apt-get, ubuntu's add/remove, synaptic, debi files, RPMs, self-build installations, and many more.  It seems like things would be much better for the linux world if there was a standard way of writing/installing applications so that developers and users don't have to worry about which distro they are using.

Will this problem be solved in the near future for linux?  Does anyone know of efforts that are being made to standardize installations and app development?

---

### Post by PresidentJFJ on 2007-07-22
After starting to use Linux, this is probably the biggest thing that I would love to have on Ubuntu. I mea, I get used to one way of installing stuff, and then BAM, have to look something up here to figure out what to do.

---

### Post by Ardrias on 2007-07-22
I sure hope it's the repos way that gets decided on in that case. I feel like crying when I'm forced to use a dist where I cant just apt-get anything.

---

### Post by strider1551 on 2007-07-22
> There's apt-get, ubuntu's add/remove, synaptic, debi files, RPMs, self-build installations, and many more.
Technically speaking, apt-get, Ubuntu's add/remove, synaptic, and .deb files are all the same from the developer's perspective.  Apt-get, add/remove, and synaptic all use .deb packages; they're just different ways of using the same thing.

Really, open source developers need to worry primarily about the source code.  Going from source code to .deb or .rpm is not that difficult, and other people normally take care of it.  I haven't been on the Linux side to know the history of package management, but I gather that .deb seems to be the most popular package method at present.  

From the user perspective, though, I completely agree.  It seems like there are hundreds of ways to install something, and every distribution has to be different.

---

### Post by Anzan on 2007-07-22
I agree that a standardized installation method, with GUI, would be good for broadening Linux usability.

By the way, does anyone know if Linspire's release of CNR is still going to involve Ubuntu?

---

### Post by geraldm on 2007-07-22
Agreed: a standard way of making packages would be beneficial to Open Source.
But: that goal seems destined never to happen.  There have been many attempts 
to develop the universal package building development application.  This has only
resulted in the proliferation of package-building applications that themselves are not subject to
standardization.  
The .deb binary package seems good in many ways, but it, too, can be criticized in that
it uses tar.gz rather than tar.bz2, which provides smaller net traffic.

Best attempt to standardize is LSB project (LSB-3.2) at freestandards.org
Mail list is lsb-discuss AT lists.freestandards.org

Gerald

---

