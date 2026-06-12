---
title: "How to keep up with the latest Kernel releases?"
date: 2006-12-07
forum: General Help
---

### Post by raid517 on 2006-12-07
Hi I have switched from Kanotix (Debian Sid) to Kubuntu.

I don't mind so much I guess not having so many packages to update - as this means at least that there are potentially less things to break.

However one thing I would like to be able to do is to keep up with the latest Kernel releases. 2.6.17 is a bit old now - and is not such a good match for my hardware (DMA doesn't work for the SATA DVD-R drive in my laptop)

One thing I could do I guess is just to download and install the latest Kernel from Kernel.org, however as far as I understand it the Ubuntu/Kubuntu kernel is quite heavily patched - so I wouldn't have a clue where to get the latest patches?

Also I'm worried that getting my Intel PRO/Wireless 3945ABG wireless chip going again, might not be such an easy task.

I did find a few Ubuntu repositories which had 2.6.19-7 kernel images in them on Google - but I haven't found anything I can add to my /etc/apt/sources.list.

In any case I did try one of these - and again my wireless stopped working - which means I assume that I also need to install additional modules from elsewhere too?

Any input on how to achieve this would be most appreciated.

---

### Post by bscbrit on 2006-12-07
To see what software is available, including kernel versions, open System -> Administration -> Synaptic.  Press 'Reload', 'Mark All Updates' and it will select the latest versions of all the software that you have installed, including kernels.  Select 'Apply' to install them.  There are other ways of doing what you want but this seems the easiest.

If you make the appropriate selections in Synaptic or using the Update icon which is usually on the top panel, it will let you know when new updates are available.

I must ask however, why do you need to chase the very latest kernels?  If your system is working then it would seem there is no essential need to update.  If you simply select the Security repositories then it will let you know when critical updates are available.  But, of course, you can manage your machine however you choose - I simply don't get paranoid about having the latest software installed providing I'm not being left vulnerable to any security problems.

---

### Post by raid517 on 2006-12-07
Yes I know about Synaptic and apt-get thanks. As I said I come from the world of Debian unstable - which I have used for a number of years.

However the officially listed/default repositories do not contain anything greater than 2.6.17x.

As far as everything working - as I indicated I am attempting to resolve an issue with the DMA settings for my SATA DVD-R drive on my new laptop - which is not fully supported in 2.6.17 - otherwise I might agree with you that there isn't much point in updating if everything works.

Unfortunately this is not true in my case.

---

### Post by Tomosaur on 2006-12-07
Not entirely sure really. You may want to take a look at Feisty Fawn, which is the next Ubuntu release. I don't know what kernel version it's starting from, but it may be a later one. Aside from that, the only option may be to just compile an 'Ubuntu' kernel yourself using the latest version, but obviously this means finding all the necessary patches and whatnot.

---

### Post by bscbrit on 2006-12-07
Sorry, I wasn't trying to talk down to you. :-# 

I've never had the need to install a kernel more recent than those offered in the repos, so I haven't got much else to suggest. I'm using 2-6-17 as well and I've not seen anything more up-to-date on offer.

It looks like you are left with the hard way.......

---

### Post by Delkster on 2006-12-07
Perhaps you could try getting the [kernel source package of Feisty](http://packages.ubuntu.com/feisty/source/linux-source-2.6.19) (the development branch of Ubuntu) and compiling it for Edgy? I'm not sure if that'd work but that's the first thing to come to my mind.

Of course there are also pre-built 2.6.19 kernels for Feisty but I'm even less sure about the binaries working directly on Edgy.

---

### Post by raid517 on 2006-12-07
Hi, thanks I already have the Feisty Linux-image-2.6.19-7-generic installed. But unfortunately my wireless does not work with this kernel version. I assume as I indicated above that this means that I might require additional modules? What modules might I require with this - and also does anyone know where I might obtain these?

Overall however I don't think it will work too well - as I tried to install the linux-headers-2.6.19-7-386 package too - and this gave me warnings about the wrong libc6 version - and also some other missing package.

Unfortunately I need the headers package as many applications will not compile without it.

On another note... If anyone does know where the latest patches can be obtained for the official kernels from Kernel.org, this would be of great help to me. Compiling and patching a kernel isn't so hard as much as it is time consuming - however it would at least give me the opportunity to look more closely at he DMA settings in the kernel for serial ATA optical drives.

---

### Post by hokiejp on 2007-01-11
A few months ago (under Breezy) I built a current kernel from source in order to get better hardware support for my laptop.  I didn't apply any special "ubuntu" patches, and as far as I know the only ones you need are the ones for your particular hardware.

I found the patches I needed (wireless, touchpad, etc.) by googling for the model name (e.g. Dell Inspiron 6000), or the name/model of the hardware.  You can build the kernel any way you like, but this page describes how to do it the "Ubuntu Way", by creating a DEB package:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

